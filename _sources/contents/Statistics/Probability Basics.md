---
html_meta:
  "description lang=en": "Interview resource of Data Science Interview focusing on Probability."
  "keywords": "interview, data science, machine learning, probability"
  "property=og:locale": "en_US"
---


## Probability Basics

```{figure} ../Statistics/images/image12.PNG
---
name: image12
scale: 100%
---
```


Probability theory is the mathematical framework that allows us to analyze chance events in a logically sound manner. The probability of an event is a number indicating how likely that event will occur.

Note that when we say the probability of a head is $1/2$, we are not claiming that any sequence of coin tosses will consist of exactly $50$% heads. If we toss a fair coin ten times, it would not be surprising to observe $6$ heads and $4$ tails, or even $3$ heads and $7$ tails. But as we continue to toss the coin over and over again, we expect the long-run frequency of heads to get ever closer to $50$%. **In general, it is important in statistics to understand the distinction between theoretical and empirical quantities. Here, the true (theoretical) probability of a head was $1/2$, but any realized (empirical) sequence of coin tosses may have more or less than exactly $50$% heads.**

### Common Terminologies

The **sample space is the set of all possible outcomes in the experiment** : for a dice $Ω = {1, 2, 3, 4, 5, 6}$.

Any **subset of $Ω$ is a valid event**. we can speak of the event $F$ of rolling a $4$, $F = {4}$.

Consider the outcome of a single die roll, and call it $X$. A reasonable question one might ask is “What is the average value of $X$?". We define this notion of “average” as a weighted sum of outcomes. This is called the **expected value**, or expectation of $X$, denoted by $E(X)$, 

$Weighted Average = \frac{1}{6} * (1 + 2 + 3 + 4 + 5 + 6) = 3.5$

If you play the game $ \infty $ times the average value becomes $E(X)$

The **variance** of a random variable $X$ is a nonnegative number that summarizes on average how much $X$ differs from its mean, or expectation.
The square root of the variance is called the **standard deviation.**

$Var(X) = \frac{(1−3.5)^2+(2−3.5)^2+(3−3.5)^2+(4−3.5)^2+(5−3.5)^2+(6−3.5)^2}{6} = \frac{17.5}{6}$

---
### Set

A set, broadly defined, is a collection of objects. In the context of probability theory, we use set notation to specify compound events. For example, we can represent the event "roll an even number" by the set {2, 4, 6}.


### Permutation and Combination

It can be surprisingly difficult to count the number of sequences or sets satisfying certain conditions. This is where **Premutation and Combination** comes in. For example, consider a bag of marbles in which each marble is a different color. If we draw marbles one at a time from the bag without replacement, how many different ordered sequences (permutations) of the marbles are possible? How many different unordered sets (combinations)? 

- Permutation($AB \neq BA$ , order matters) = $nPr = \frac{n!}{(n-r)!}$
- Combination($AB = BA$ , order does not matter) = $nCr = \frac{n!}{r!(n-r)!}$

### Joint & Conditional Probability

- Joint Probability is the probability of $2$ independent events occuring : $P(A \cap B) = P(A)*P(B)$
- Conditional probability tells the probability of $B$ given $A$ has occured, it allow us to account for information we have about our system of interest: $P(B|A) = \frac{P(A \cap B)}{P(A)}$

**If both are same then A and B are independent events.**

### Bayes' Theorem

Bayes' theorem, named after 18th-century British mathematician Thomas Bayes, is a mathematical formula for determining conditional probability. **Conditional probability is the likelihood of an outcome occurring, based on a previous outcome occurring.**

```{figure} ../Statistics/images/image1.PNG
---
height: 150px
name: image1
---
Baye's Theorem
```

An easy way of remembering it is using the below example:

What is the probability of a fruit being banana given that it is long, sweet and yellow?

$P(Banana|Long,Sweet,Yellow) = \frac{P(Long|Banana)*P(Sweet|Banana)*P(Yellow|Banana)*P(Banana)}{P(Long)*P(Sweet)*P(Yellow)}$

---
### Questions

```{admonition} Problem: [UBER] Dice in increasing order
:class: tip, dropdown

We throw 3 dice one by one. What is the probability that we obtain 3 points in strictly increasing order?

```

```{admonition} Solution:
:class: dropdown

Suppose we get $4$ in the first roll then,

Total Probability = $P(4) * P(5) * P(6) = 1/6 * 1/6 * 1/6 = 1/216$

Similarly for $3$,    $P(3) * P(4,5 | 4,6 | 5,6) = 1/6 * (1/36 + 1/36 + 1/36) = 3/216$

Taking into consideration $P(1)$ and $P(2)$ we have the total as $= 10/216 + 6/216 + 3/216 + 1/216 = 20/216$ 

```

```{admonition} Problem: [LINKEDIN] Cards in increasing order
:class: tip, dropdown

Imagine a deck of $500$ cards numbered from $1$ to $500$. If all the cards are shuffled randomly and you are asked to pick three cards, one at a time, what's the probability of each subsequent card being larger than the previous drawn card?
```

```{admonition} Solution:
:class: dropdown

It is actually easy to solve this if you think on it a little. Let's pick any $3$ cards, now if you rearrange it there will only be $1$ way in which each subsequent card is larger the previous card. So a total of $6$ ways to arrange the cards out of which only $1$ is valid. So the result is $\frac{1}{6}$.
```


```{admonition} Problem: [STATE FARM] Cards without replacement
:class: tip, dropdown

Pull $2$ cards from a deck without replacement what is probability that both are of different colors.

There can be many variants to this question.

```

```{admonition} Solution:
:class: dropdown
 
$52$ cards = $26$ Red + $26$ Black

- Different Color Without Replacement $= 26/52 * 26/51$
- Different Color With Replacement    $= 26/52 * 26/52$
- Same Color Without Replacement 	  $= 26/52 * 25/51$
- Same Color With Replacement    	  $= 26/52 * 25/52$
```

```{admonition} Problem: [FACEBOOK] N Dice
:class: tip, dropdown

Suppose you're playing a dice game. You have 2 die.

- What's the probability of rolling at least one 3?
- What's the probability of rolling at least one 3 given N die?
```

```{admonition} Solution:
:class: dropdown

P(at least 1 three) $=$ P(exactly 1 three) $+$  P(2 three) $= 1/6 * 5/6 + 5/6 * 1/6 + 1/36 = 11/36$

The second part of the question is a little tricky, let's start by generalizing the above equation:

P(at least 1 three) $= 2*(5^1/6^2) + 5^0/6^2$

Now for N dice: P(at least 1 three) $=$ P(exactly 1 three) $+$  P(2 three) $+$  P(3 three) ... $+$  P(N three)

Combining both $= N * \frac{5^{N-1}}{6^N} + N * \frac{5^{N-2}}{6^N} + N * \frac{5^{N-3}}{6^N} + ... + N * \frac{5^0}{6^N} = \frac{N}{6^N}(5^{N-1} + 5^{N-2} + .. + 1)$

```

```{admonition} Problem: [FACEBOOK] 3 Zebras
:class: tip, dropdown

Three zebras are chilling in the desert. Suddenly a lion attacks.

Each zebra is sitting on a corner of an equally length triangle. Each zebra randomly picks a direction and only runs along the outline of the triangle to either edge of the triangle.

What is the probability that none of the zebras collide?
```

```{admonition} Solution:
:class: dropdown

Each zebra has 2 options of travel: clockwise or anticlockwise. So a total of $2*2*2 = 8$ options.

Out of this only way in which they donot collide is if all of them travel clockwise or anticlockwise. So a total of $2$.

Therefore the probability of no collision $= 2/8 = 25%$

```

```{admonition} Problem: [POSTMATES] Four Person Elevator
:class: tip, dropdown

There are four people on the ground floor of a building that has five levels not including the ground floor. They all get into the same elevator.

If each person is equally likely to get on any floor and they leave independently of each other, what is the probability that no two passengers will get off at the same floor?

```

```{admonition} Solution:
:class: dropdown

The number of ways to assigning five floors to four different people is to get the total sample space. In this case it would be $5 * 5 * 5 * 5$.

The number of ways to assign five floors to four people without repetition of floors is $5 * 4 * 3 * 2$ because for the first passenger you have five different options. The second person has four, and so on. Note that this number counts all possible orders between passengers as well.

The result is then $\frac{5 * 4 * 3 * 2}{5 * 5 * 5 * 5} = 0.192$
```

```{admonition} Problem: [AMAZON] Found Item
:class: tip, dropdown

Amazon has a warehouse system where items on the website are located at different distribution centers across a city. Let's say in one example city, the probability that a specific item X at location A is 0.6, and at location B the probability is 0.8.

Given you're a customer in this example city and the items are only found on the website if they exist in the distribution centers, what is the probability that the item X would be found on Amazon's website?

```

```{admonition} Solution:
:class: dropdown
Probability of the item being present= $1-$ p(item NOT in A AND NOT in B) $= 1-(0.4*0.2)=0.92$
```

```{admonition} Problem: [SPOTIFY] Max Dice Roll
:class: tip, dropdown

A fair die is rolled $n$ times. What is the probability that the largest number rolled is $r$, for each $r$ in $1..6$?
```

```{admonition} Solution:
:class: dropdown
If $r(1≤r≤6)$ is the largest number you have allowed for your $n$ rolls, then you forbid any number larger than $r$. That is, you forbid $6−r$ values. The probability that your single roll does not show any of these $6−r$ values is $\frac{6−r}{6}$ and the probability that this happens each time during a series of $n$ rolls is the obviously $(\frac{6−r}{6})^n$
```

```{admonition} Problem: [FACEBOOK] Labeling Content
:class: tip, dropdown

Facebook has a content team that labels pieces of content on the platform as spam or not spam. $90%$ of them are diligent raters and will label $20%$ of the content as spam and $80%$ as non-spam. The remaining $10%$ are non-diligent raters and will label $0%$ of the content as spam and $100%$ as non-spam. Assume the pieces of content are labeled independently from one another, for every rater. Given that a rater has labeled $4$ pieces of content as good, what is the probability that they are a diligent rater?
```

```{admonition} Solution:
:class: dropdown

This can be solved using Baye's theorem:

- Not Spam = $NS$
- Spam = $S$
- Diligent =$D$
- NotDiligent =$ND$

$P(D|NS, NS, NS, NS) = \frac{P(NS, NS, NS, NS|D)*P(D)}{P(NS, NS, NS, NS|D)*P(D)+P(NS, NS, NS, NS|ND)*P(ND)}$
$P(D|NS, NS, NS, NS) = \frac{0.8^4*0.9}{0.8^4*0.9+1^4*0.1}$ = ~$0.787$
```

```{admonition} Problem: [FACEBOOK] Raining
:class: tip, dropdown

You are about to get on a plane to Seattle. You want to know if you should bring an umbrella. You call $3$ random friends of yours who live there and ask each independently if it's raining. Each of your friends has a $2/3$ chance of telling you the truth and a $1/3$ chance of messing with you by lying. All $3$ friends tell you that "Yes" it is raining.

What is the probability that it's actually raining in Seattle?
```

```{admonition} Solution:
:class: dropdown

Even though the problem is straightforward one can interpret the problem in many ways. Taking a Bayesian approach is probably appropriate in a real world sense, but if you are told by the interviewer you have no ability to determine the priors, you can't use Bayesian. [Check this thread](https://math.stackexchange.com/questions/1335235/facebook-question-data-science) for a detailed discussion on this problem.

For it to be not raining, all friends must be lying. Therefore, the solution must be the inverse of the probability that all three are "messing with you." 
$(1/3)x(1/3)*(1/3)=1/27$ (3.7% chance they are all lying). 

Since there is only a $3.7%$ chance all three friends are messing with you, there is a $96.3%$ chance it is raining.
```

```{admonition} Problem: [MICROSOFT] First to Six
:class: tip, dropdown

Amy and Brad take turns in rolling a fair six-sided die. Whoever rolls a $6$ first wins the game. Amy starts by rolling first.

What's the probability that Amy wins?
```

```{admonition} Solution:
:class: dropdown
Amy can win on the first roll, third roll, fifth roll, and so on.

Probability of Amy winning in the first roll = P(six rolled by her) = $1/6$

Probability of Amy winning in the third roll = P(six NOT rolled by her in first try) * P(six NOT rolled by Brad in first try) * P(six rolled by her in 2nd try) = $(5/6) * (5/6) * (1/6) = 1/6 * (5/6)^2$

Similarly, the probability of Amy winning in the fifth roll = $(1/6) * (5/6)^4$

Similarly, the probability of Amy winning in the seventh roll = $(1/6) * (5/6)^6$

Hence, total probability of Amy winning = Sum of all such events = $(1/6) + (1/6 * (5/6)^2) + (1/6 * (5/6)^4) + (1/6 * (5/6)^6) + ...$

The sum of such an infinite Geometric Progression series is = $\frac{a}{1-r} = (1/6) / (1 - 25/36) = (1/6) / (11/36) = 6/11$

Hence, probability of Amy winning in any of her turns = $6/11$
```

