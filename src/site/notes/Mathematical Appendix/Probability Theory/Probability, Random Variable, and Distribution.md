---
{"dg-publish":true,"permalink":"/mathematical-appendix/probability-theory/probability-random-variable-and-distribution/"}
---


#math #measure #probability #stat

*Oh, Hyunzi. (email: wisdom302@naver.com)*
*Korea University, Graduate School of Economics.*

---
**Main References**
- Kim, Dukpa. (2024). "Econometric Analysis" (2024 Spring) ECON 518, Department of Economics, Korea University.
- Capinski and Kopp. (2003). "Measure, Integral and Probability" (2nd edition)
- Hogg et al. (2013). "Introduction to Mathematical Statistics" (8th Edition)
---

Here, we briefly introduce more rigorous definitions of the probability theory based on the measure theory. The main goal of this note is to understand the concept of probability measure intuitively, and get familiar with the jargon of measure theory. The detailed theorems and results of the measure theory used in this section will be further analyzed in [[Mathematical Appendix/Measure Theory/Measure\|Measure]], with mathematical proofs.

# Probability

## Probability Space

The goal of this note is to fully understand the concepts of the key elements consisting the probability space.

>[!def] probability space
>A **probability space** is the triple $(\Omega, \mathcal{F}, P)$ consists of three elements:
> 1. A **sample space**, $\Omega$, is the set of all possible outcomes of a random experiment. An element of $\Omega$ is $\omega$, which is called an outcome.
> 2. An **event space**, $\mathcal{F}$, is a collection of all subsets of $\Omega$, called a *$\sigma$-field*. An element of $\mathcal{F}$ is $E$, which is called an event.
> 3. A **probability function (measure)**, $P$, assigns each event to a **probability**, which is a number between $0$ and $1$.{ #a919fa}


In later chapter [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#Probability Measure\|#Probability Measure]], we will discuss about how to understand [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^27dce2\|$\sigma-$field]] and [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^58f06f\|measure]]. Before that, we first review some of the key definitions we studied in [[Mathematical Appendix/Probability Theory/Statistical Proof\|Mathematical Statistics]].


>[!def] probability
>A set function $P$ on $\mathcal{F}$ is a **probability** or **probability measure** if it satisfies:
> 1) $P(E)\geq 0$, for all $E \in \mathcal{F}$.
> 2) $P(\Omega)=1$.
> 3) If $E_{1}, E_{2}, \cdots \in \mathcal{F}$ are disjoint, then we have $$P\left( \bigcup_{i=1}^{\infty}E_{i} \right)=\sum_{i=1}^{\infty}P(E_{i}).$$

>[!exm] tossing a coin
>Consider an experiment of tossing a coin. The two possible outcomes are head($H$) and tail$(T)$. Therefore, the sample space is $$\Omega = \{ H, T \}$$and the event space is $$\mathcal{F}= \{ \emptyset, \{H\}, \{T\}, \{H, T\} \}.$$By definition, we have $P(\{H, T\})=1$, implying that $P(\emptyset)=0$. If the coin is a fair one, then we would also have $P(\{T\})=P(\{H\})= \frac{1}{2}$.


>[!def] conditional probability
>For an event $F$ such that $P(F)>0$, the *conditional probability* of $E$ given $F$ is defined by $$P(E|F) = \frac{P(E\cap F)}{P(F)},$$which function is also a probability (measure).

## Random Variables

Let a probability space $(\Omega, \mathcal{F}, P)$ be given for the rest of this section.


>[!def] random variable
>A **random variable** $X$ is a *measurable function* from $\Omega$ to $\mathbb{R}$. i.e, it assigns a real number to each outcome.{ #1a47b9}


>[!rmk] measureable function
>A function $X: \Omega \rightarrow \mathbb{R}$ is **measurable** if $$X^{-1}(A)= \{\omega \in \Omega| \ X(\omega) \in A\}\in \mathcal{F}, \quad \forall A \in B(\mathbb{R}),$$where $B(\mathbb{R})$ is called the *Borel sets*.{ #1baba0}


Here, you can simply understand the Borel sets as a collection of subsets of the real line. A detailed explanations follows in [[Mathematical Appendix/Measure Theory/Borel Measure\|Borel Measure]]. Now we define a probability (measure) on $B(\mathbb{R})$, 


>[!exm] tossing a coin 2
>In the given sample space $$\Omega= \{ H, T \},$$we may define a random variable $X$ by $X(H)=1$ and $X(T)=0$.

A random variable is simply a mapping that maps each outcome to a real number where we can use well developed mathematical tools. 

We now re-define some of the familiar concepts.


## Distribution and Density Function

>[!def] distribution
>A **distribution** $P_{X}$ of a random variable $X$ is the probability (measure) on $(\mathbb{R}, B(\mathbb{R}))$ induced by $X$: $$P_{X}(A) = P(X^{-1}(A))= P(\{ \omega \in \Omega| \ X(\omega)\in A \}).$$


>[!def] distribution function
>A **(cumulative) distribution function** $F_{X}$ of a random variable $X$ is defined as $$F_{X}(x) = P_{X}(-\infty, x].$$
>If $X$ is a *continuous* random variable, then $$F_{X}(x) = \int_{-\infty}^{x}f_{X}(t) \ dt, \quad \forall x.$$
>If $X$ is a *discrete* random variable, then $$P(X=b)=F_{X}(b)-\lim_{x \rightarrow b^{-}}F_{X}(x).$${ #9e83b8}



>[!prp] properties of distribution function
> 1. non-decreasing: $$x_{1} \leq x_{2} \quad \Rightarrow \quad F_{X}(x_{1}) \leq F_{X}(x_{2}).$$
> 2. limit value: $$\lim_{x \rightarrow \infty}F_{X}(x)=1, \quad \lim_{x \rightarrow -\infty}F_{X}(x)=0.$$
> 3. continuity when increasing: $$\text{if } x \geq x_{0}, \qquad x \rightarrow x_{0} \quad \Rightarrow \quad F_{X}(x) \rightarrow F_{X}(x_{0}).$$
> 4. expectation: $$\mathbb{E}(X) = \int_{0}^{\infty} P(X > t) \ dt.$$


>[!def] probability mass function
>A **probability mass function (pmf)** $p_{X}$ is the probability distribution of a *discrete* random variable: $$p_{X} (x)= P(X=x).$$

The density function of a continuous variable is more tricky to define.


>[!def] absolutely continuous and density
>If a measure $P: \mathcal{F} \rightarrow \mathbb{R}$ satisfies $$P(A)= \int_{A}f \ d \mu$$for every integrable function $f \geq 0$, then $P$ is **absolutely continuous**. Here such $f$ is called as a **density** of $P$ for a measure $\mu$.

Note that the absolute continuity of $P$ is a result from a property of the measure, which itself is continuous. While we will further look into the definition later on, here, you can simply understand as a characteristic of the integral.


>[!def] probability density function
>A **probability density function (pdf)** $f_{X}$ of a *continuous* random variable $X$ is the function that satisfies $$F_{X}(x) = \int_{-\infty}^{x}f_{X}(t) \ dt.$$

---

# Probability Measure

## Sigma-Algebra

First, we follow the previous notions of the sample space and the set of all events denoted $\Omega$ and $\mathcal{F}$, respectively. Obviously, $\mathcal{F}$ is a collection of subsets of $\Omega$, a set of sets (i.e. family of sets). An typical example of an event set is the power set $2^{\Omega}$, which collects all the subsets of $\Omega$.

A sigma-algebra is a subset of the poser set $2^{\Omega}$, which is therefore a family of sets in $\mathcal{F}$, that satisfies certain properties.


>[!def] sigma-algebra and measurable space
>For a sample space $\Omega$, the set of all events $\mathcal{F}\subset 2^{\Omega}$ is **$\sigma$-algebra** or **$\sigma$-field** on $\Omega$, if the following conditions are satisfied:
> 1. $\emptyset, \Omega \in \mathcal{F}$: *inclusion of empty set and the entire set*.
> 2. $\forall E \in \mathcal{F}$, $E^{c}=\Omega \setminus E \in \mathcal{F}$: *closed under complements*.
> 3. $\forall \{E_{n}\}_{n \in \mathbb{N}_{+}}\subset \mathcal{F}$, $E=\cup_{n}E_{n}\in \mathcal{F}$: *closed under countable unions*. 
>
>For $\mathcal{F}$, which is a $\sigma$-algebra on $\Omega$, an ordered pair of $(\Omega, \mathcal{F})$ is called a **measurable space**.{ #27dce2}



Here, note that the term 'sigma-' in mathematics usually implies 'countable union' or 'countably infinite'. Thus, $\sigma$-algebra means it is closed under the countable union, i.e., it contains every countable union of itself. 

Furthermore, since countable set is isomorphic to $\mathbb{N}$, meaning that there exists an one-to-one correspondence between the two, we can understand $\sigma$-algebra as the set consists the countably infinite number of the subsets of $\Omega$, where we can index the each of the subsets in natural number bases.


>[!exm] example of sigma-algebra and induced algebra
>Let $X=\{1, 2, 3, 4\}$. Then the $\sigma$-algebra of $X$ can be  $$\begin{align} F_{0}&= \{\emptyset, \{1, 2, 3, 4\} \}, \\ F_{1}&=  \{ \emptyset, \{1, 2\}, \{3, 4\}, \{1, 2, 3, 4\} \},\\ F_{2}&= \{\emptyset , \{1\}, \{2\}, \{1, 2\}, \{3, 4\}, \{1, 3, 4\}, \{2, 3, 4\}, \{1, 2, 3, 4\}\}, \end{align}$$and many others. Here, $F_{2}$ is a $\sigma$-algebra of $X$ *induced* by the set $B=\{\{1\}, \{2\} \}$, meaning that $F_{2}$ is a $\sigma$-algebra containing $B$.

## Measure

For some $\sigma$-algebra $\mathcal{F}$ which is defined on $\Omega$, a *measure* is a function that assigns each events $E \in \mathcal{F}$ to a non-negative real numbers: $$\mu: \mathcal{F} \rightarrow [0, \infty).$$Intuitively, this set function is a generalization and formalization of geometrical measures (length, area, and volume) and other common notions (magnitude, mass, and probability). More simply, we can understand the concept of a measure as a set function that *measures* the size of the given set.


>[!def] measure and measure space
>Let $\Omega$ be a sample space and $\mathcal{F}$ be a $\sigma$-algebra over $\Omega$. A set function $\mu: \mathcal{F} \rightarrow [0, \infty)$ is called a **measure** if the following conditions hold:
> 1. $\forall E \in \mathcal{F}$, $\mu(E)\geq 0$: *non-negativity*.
> 2. $\mu(\emptyset)=0$: *empty set with measure $0$*.
> 3. For any disjoint countable collection $\{E_{n}\}_{n\in \mathbb{N}_{+}}$, of $E_{n} \in \mathcal{F}, \forall n$, we have $$\mu\left( \bigcup_{n=1}^{\infty}E_{n} \right)= \sum_{n=1}^{\infty}\mu(E_{n}),$$: *countable additivity*.
>
> And a triple $(\Omega, \mathcal{F}, \mu)$ is called a **measure space**.{ #58f06f}



Here, the countable additivity is the key property that makes a measure a generalized length.


>[!prp] properties of measure
>Let $\mu$ be a measure. The following properties directly follows from the definition.
> 1. monotonicity: If $E_{1}, E_{2}$ are measurable sets with $E_{1} \subseteq E_{2}$, then $$\mu(E_{1}) \leq \mu(E_{2}).$$
> 2. continuity from below: If $E_{1} \subseteq E_{2}\subseteq \cdots$ are measurable sets that are increasing, then the union of the sets $E_{n}$ is measurable and $$\mu\left( \bigcup_{i=1}^{\infty}E_{i} \right)= \lim_{i \rightarrow \infty}\mu(E_{i})= \sup_{i \geq 1}\mu(E_{i}).$$
> 3. continuity from above: If $E_{1} \supseteq E_{2}\supseteq \cdots$ are measurable sets that are decreasing, then the intersection of the sets $E_{n}$ is measurable. Furthermore, if at least one of the $E_{n}$ has finite measure then $$\mu\left( \bigcap_{i=1}^{\infty}E_{i} \right)= \lim_{i \rightarrow \infty}\mu(E_{i})= \inf_{i \geq 1}\mu(E_{i}).$$

From the definition of [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^58f06f\|measure]], by adding one more property, we finally have the definition of the probability measure.


>[!def] probability measure and probability space
>Let $\Omega$ be a sample space and $\mathcal{F}$ be a $\sigma$-algebra over $\Omega$. A set function $P: \mathcal{F} \rightarrow [0, 1]$ is called a **probability measure** if the following conditions hold:
> 1. $\forall E \in \mathcal{F}$, $P(E)\geq 0$: *non-negativity*.
> 2. $P(\emptyset)=0$: *empty set with measure $0$*.
> 3. For any disjoint countable collection $\{E_{n}\}_{n\in \mathbb{N}_{+}}$, of $E_{n} \in \mathcal{F}, \forall n$, we have $$P\left( \bigcup_{n=1}^{\infty}E_{n} \right)= \sum_{n=1}^{\infty}P(E_{n}),$$: *countable additivity*.
> 4. $P(\Omega)=1$: **total mass is 1**.
>
> And the triple $(\Omega, \mathcal{F}, P)$ is called as a **probability space**.
{ #2c8d7a}


## Measurable Sets

>[!def] measurable set
>Let $(\Omega, \mathcal{F})$ be a measurable space. Then a subset $S \subseteq \Omega$ is said to be **($\mathcal{F}$-)measurable** if $S \in \mathcal{F}$.{ #b3caaa}



>[!rmk] null set
>A measurable set $X$ is *null set* if $\mu(X)=0$. 
{ #fd9cb0}



>[!def] length and null set
>Let $\mathcal{I}$ a set of open intervals in real line, and define a function $l: \mathcal{I} \rightarrow [0, \infty)$ such that $$l(I) := \sup I - \inf I, \quad I \in \mathcal{I},$$and denote the function $l(\cdot)$ as *length*. Then, a set $A\in \mathbb{R}$ is called **null set** if there exists a sequence of open interval $\{I_{n}: n \in \mathbb{N}\}$ such that $$A \subset \bigcup_{n=1}^{\infty}I_{n},\quad \sum_{n=1}^{\infty}l(I_{n})< \varepsilon,$$for every $\varepsilon>0$.

Compared to the empty set, null set refers to the set which is practically non-existing, while empty set denotes the set which is actually empty. Here, the null means meaningless, insignificance, or negligible, rather then the absence.


>[!prp] theorems of null set
> 1. empty set is null set.
> 2. any set of a single element is null set.
> 3. any countable set is null set.

>[!def] almost surely
>Let $(\Omega, \mathcal{F}, P)$ be a probability space. An event $E\in \mathcal{F}$ happens **almost surely** if $P(E)=1$. Equivalently, $E$ happens almost surely if the probability of $E$ not occurring is zero: $P(E^{c})=0$.{ #521938}


Intuitively, 'almost surely' refers to the every point except the null set. This concept is similar to the integral where $\int_{a}^{a}f(x) dx=0$, and also to the probability where we does not care whether the end points of the set is included or not.


>[!def] almost surely converges
>The sequence of random vectors $\{X_{n}\}$ **converges almost surely**, i.e. $$X_{n} \xrightarrow[]{a.s.}X$$if $$P(\{\omega \in \Omega : \ X_{n} \rightarrow X\})=1.$$ 
{ #4fba4c}


Note that in [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^4fba4c\|#^4fba4c]], we do not care about the timing when $X_{n}$ enters to the neighborhood of $X$ and remains there forever. Thus we introduce further concepts.


>[!def] event eventually and infinitely often
>Let $(\Omega, \mathcal{F}, P)$ be a probability space, and let $\{E_{n}\}_{n \in \mathbb{N}_{+}}$ be a sequence of events in $\mathcal{F}$. Then **events eventually (e.v.)** denotes the chance of happening $E_{n}$ in infinite horizon of time: $$\begin{align} \{E_{n} \ e.v.\} &=  \{\omega \in \Omega: \ \exists N \geq0, \forall n \geq N, \  \omega \in E_{n} \} \\ &= \bigcup_{N=1}^{\infty} \bigcap_{n \geq N} E_{n}= \lim_{n \rightarrow \infty}\inf E_{n}. \end{align}$$Using De Morgan's law, the opposite case is **infinitely often (i.o.)**, the chance that will not violate the given $E_{n}$ in infinite horizon of time: $$\begin{align} \{E_{n} \ i.o.\} &=  \{\omega \in \Omega: \ \omega \in E_{n} \text{ infinitely many }n \} \\ &= \bigcap_{N=1}^{\infty} \bigcup_{n \geq N} E_{n}= \lim_{n \rightarrow \infty}\sup E_{n}. \end{align}$$

Here, the term e.v. and i.o. emphasizes that in terms of convergence in a sequence, the only important thing is the long-term behavior, not the behavior in the first finite horizon of the time. 


>[!rmk] almost sure convergence, and ev and io
Define a sequence of sets as $E_{n} := \{\omega : |X_{n}(\omega) - X(\omega)| < \varepsilon\}$. Then, $X_{n} \xrightarrow[]{a.s.}X$, if the probability that $E_{n}$ events eventually is equals to $1$: $$\forall \varepsilon>0, \quad P(\{E_{n} \ e.v.\})=P\left( \bigcup_{N=1}^{\infty} \bigcap_{n \geq N} \big\{ \omega : \ |X_{n}(\omega)-X(\omega)| < \varepsilon \big\} \right)=1,$$which condition is equivalent to $$\forall \varepsilon>0, \quad P(\{E_{n} \ i.o.\})=P\left( \bigcap_{N=1}^{\infty} \bigcup_{n \geq N} \big\{ \omega : \ |X_{n}(\omega)-X(\omega)| > \varepsilon \big\} \right)=0,$$i.e. the probability that $E_{n}$ happens infinitely often is equals to $0$.{ #2ff43b}



Usually, [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^2ff43b\|#^2ff43b]] is another common way to define [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^4fba4c\|#^4fba4c]]. For the brief understanding, suppose $X_{n} \rightarrow X$ pointwise and let $\omega' \in \{\omega \in \Omega | \ X_{n}(\omega) \rightarrow X(\omega) \}$. By the definition, $$\forall \varepsilon>0, \ \exists N_{\omega'}\geq0, \ \forall n \geq N_{\omega'}, \quad |X_{n}(\omega)- X(\omega)| < \varepsilon,$$for all $\omega\in \Omega$. 
Thus we have $$\omega' \in \bigcap_{n \geq N_{\omega'}} \big\{ \omega : \ |X_{n}(\omega)-X(\omega)| < \varepsilon \big\}.$$Alternatively, $$\bigcup_{N=1}^{\infty} \bigcap_{n \geq N} \big\{ \omega : \ |X_{n}(\omega)-X(\omega)| < \varepsilon \big\}, \ \forall \varepsilon>0 \ \ = \ \ \{ \omega : \ X_{n}(\omega) \rightarrow X(\omega) \},$$resulting in the definition of almost sure convergence. For the infinitely often part, it can be easily driven using De Morgan's law.


---

# Random Variable
## Measurable Functions

Intuitively, a measurable function is a function between the two [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^27dce2\|measurable space]] that preserves the structure of the spaces. Here, the inverse image of any measurable function is [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^b3caaa\|measurable]]. 


>[!def] measurable function
>Let $(\Omega, \mathcal{F})$ be a measurable space, and for a function $f:\Omega \rightarrow \bar{\mathbb{R}}$, define a set $$S_{f}(\alpha):=  \{\omega\in \Omega | \ f(\omega)> \alpha \} = f^{-1}\big((\alpha, \infty)\big), \quad \forall \alpha \in \mathbb{R}.$$Then, $f$ is **$\mathcal{F}-$measurable** if for all $\alpha \in \mathbb{R}$, $S_{f}(\alpha) \in \mathcal{F}$.{ #03f1b6}


It is shown that it is equivalent to show the following conditions to prove the given function is measurable.


>[!prp] equivalent conditions to measurable function
>For a function $f: \Omega \rightarrow \bar{\mathbb{R}}$, the following conditions are equivalent:
> 1) $\forall \alpha \in \mathbb{R}$, $\{\omega \in \Omega| \ f(\omega) > \alpha\} = f^{-1}\big((\alpha, \infty)\big) \in \mathcal{F}$
> 2) $\forall \alpha \in \mathbb{R}$, $\{\omega \in \Omega| \ f(\omega) \leq \alpha\}= f^{-1} \big((-\infty, a]\big) \in \mathcal{F}$
> 3) $\forall \alpha \in \mathbb{R}$, $\{\omega \in \Omega| \ f(\omega) \geq \alpha\} = f^{-1}\big([a, \infty)\big) \in \mathcal{F}$
> 4) $\forall \alpha \in \mathbb{R}$, $\{\omega \in \Omega| \ f(\omega) < \alpha\}= f^{-1}\big((-\infty, a)\big) \in \mathcal{F}${ #fb27d5}


`\begin{proof}`As 1 and 2 are complement to each other, similarly, 3 and 4 are complement to each other. By [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^27dce2\|#^27dce2]], 1 and 2, and 3 and 4 are equivalent conditions (since the complement set of the element in $\sigma-$algebra is also its element). Thus it is sufficient to show that 1 and 3 are equivalent condition, since 1 is a given definition from [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^03f1b6\|#^03f1b6]]. Below, we first show that 1 implies 3, and then we show the converse. 

($\Rightarrow$) Assume for a function $f$, we have $$\forall \alpha \in \mathbb{R}, \qquad A_{\alpha}:=\{\omega \in \Omega| \ f(\omega) > \alpha\}  \in \mathcal{F}.$$Then we have $$\forall n \in \mathbb{N}, \quad A_{\alpha- \frac{1}{n}}= \left\{\omega \in \Omega | \ f(\omega) > \alpha- \frac{1}{n}\right\} \in \mathcal{F},$$since $A_{\alpha- \frac{1}{n}} \subseteq A_{\alpha-1}$, and 1 holds for every $\alpha$. Since $$C_{\alpha} := \{ \omega\in \Omega| \ f(\omega)\geq \alpha \}= \bigcap_{n=1}^{\infty}A_{\alpha - \frac{1}{n}},$$and $\sigma-$field is closed under every intersection, we have $C_{\alpha} \in \mathcal{F}$.

($\Leftarrow$) Assume for a function $f$, we have $$\forall \alpha \in \mathbb{R}, \qquad C_{\alpha}:=\{\omega \in \Omega| \ f(\omega) \geq \alpha\}  \in \mathcal{F}.$$Then we have $$\forall n \in \mathbb{N}, \quad C_{\alpha + \frac{1}{n}}= \left\{\omega \in \Omega | \ f(\omega) \geq \alpha+ \frac{1}{n}\right\} \in \mathcal{F},$$and $$A_{\alpha}= \bigcup_{n=1}^{\infty}C_{\alpha+ \frac{1}{n}} \in  \mathcal{F},$$as $\sigma-$field is closed under every union. `\end{proof}`



Remark that [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^03f1b6\|#^03f1b6]] is analogue to [[Mathematical Appendix/Topology/Basic Topology#^1bc20f\|Basic Topology#^1bc20f]], which gives the sense of the *preserving* properties of the measurable function. 

For your information, measurable function can be defined in more fundamental way, not directly defining from its inverse-image. In that case, we can also derive the same property of [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^03f1b6\|#^03f1b6]]. 

Furthermore, measurable function can alternatively obtained from the pointwise convergence of the sequence of simple functions.



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



#math #measure #topology

*Oh, Hyunzi. (email: wisdom302@naver.com)*
*Korea University, Graduate School of Economics.*

---
**Main References**
- Capinski and Kopp. (2003). "Measure, Integral and Probability" (2nd edition)
- Rudin. (1976). "Principles of Mathematical Analysis" (3rd Edition)
- [jjycjn's Math Storehouse - 위상수학이란 무엇일까?](https://jjycjnmath.tistory.com/150)
- [생새우초밥집 - 측도론](https://freshrimpsushi.github.io/ko/)
---


# Classes of Subsets

## Family of Sets

>[!def] Family of Sets
>- **set**: well-defined collection of objects
>- **family** of sets: the set whose elements are sets
>- **member**: an element of family
>- **index**: if every set $A_\gamma$ corresponds to each $\gamma\in \Gamma$, then $\gamma$ is defined as an index, $\Gamma$ as an index set, and $\{A_{\gamma}:\gamma\in \Gamma\}$ as an index family.

note that 'family' is not an exact concept as set. for instance, $\mathcal{F}=\{\{1\}, \mathbb{R}, \mathbb{Q}, \emptyset, \mathbb{R}\}$is also a family while $\mathbb{R}$ occurs twice. 

- union of all sets: $\bigcup \mathcal{F} = \bigcup_{A\in \mathcal{F}}\{ x \in U: \exists A \in \mathcal{F}, x \in A \}$
- intersection of all sets: $\bigcap \mathcal{F} = \bigcap_{A\in \mathcal{F}}\{ x \in U: \forall A \in \mathcal{F}, x \in A \}$
for $\{A_{\gamma}: \gamma\in \Gamma \}$, we have the following properties:
1. Vacuous Truth: for universal set $U$, $\bigcup_{\gamma\in \emptyset}A_{\gamma}= \emptyset, \quad \bigcap_{\gamma\in \emptyset}A_{\gamma}= U.$
2. De Morgan law: $\left( \bigcup_{\gamma \in \Gamma} A_{\gamma} \right)^{c}= \bigcap_{\gamma \in \Gamma} A_{\gamma}^{c}, \quad \left( \bigcap_{\gamma \in \Gamma} A_{\gamma} \right)^{c}= \bigcup_{\gamma \in \Gamma} A_{\gamma}^{c}.$
3. distributive law: $\begin{align} \left( \bigcup_{\gamma \in \Gamma} A_{\gamma} \right) \cap B = \bigcup_{\gamma \in \Gamma} \left( A_{\gamma}\cap B \right), \\ \left( \bigcap_{\gamma \in \Gamma} A_{\gamma} \right) \cup B = \bigcap_{\gamma \in \Gamma} \left( A_{\gamma}\cup B \right). \end{align}$

>[!def] sigma-algebra and measurable space
>For a Given set $X$, the set of all events $\mathcal{F}\subset 2^{X}$ is **$\sigma$-algebra** or **$\sigma$-field** on $X$, if the following conditions are satisfied:
> 1. $\emptyset, X \in \mathcal{F}$: *inclusion of empty set and the entire set*.
> 2. $\forall E \in \mathcal{F}$, $E^{c}=X \setminus E \in \mathcal{F}$: *closed under complements*.
> 3. $\forall \{E_{n}\}_{n \in \mathbb{N}_{+}}\subset \mathcal{F}$, $E=\cup_{n}E_{n}\in \mathcal{F}$: *closed under countable unions*. 
>
>For $\mathcal{F}$, which is a $\sigma$-algebra on $X$, an ordered pair of $(X, \mathcal{F})$ is called a **measurable space**.

# Measure

For some $\sigma$-algebra $\mathcal{F}$ which is defined on $X$, a *measure* is a function that assigns each events $E \in \mathcal{F}$ to a non-negative real numbers: $\mu: \mathcal{F} \rightarrow [0, \infty).$Intuitively, this set function is a generalization and formalization of geometrical measures (length, area, and volume) and other common notions (magnitude, mass, and probability). More simply, we can understand the concept of a measure as a set function that *measures* the size of the given set.


>[!def] measure and measure space
>Let $X$ be a sample space and $\mathcal{F}$ be a $\sigma$-algebra over $X$. A set function $\mu: \mathcal{F} \rightarrow [0, \infty)$ is called a **measure** if the following conditions hold:
> 1. $\forall E \in \mathcal{F}$, $\mu(E)\geq 0$: *non-negativity*.
> 2. $\mu(\emptyset)=0$: *empty set with measure $0$*.
> 3. For any disjoint countable collection $\{E_{n}\}_{n\in \mathbb{N}_{+}}$, of $E_{n} \in \mathcal{F}, \forall n$, we have $\mu\left( \bigcup_{n=1}^{\infty}E_{n} \right)= \sum_{n=1}^{\infty}\mu(E_{n}),$: *countable additivity*.
>
> And a triple $(X, \mathcal{F}, \mu)$ is called a **measure space**.

Here, the countable additivity is the key property that makes a measure a generalized length.


>[!prp] properties of measure
>Let $\mu$ be a measure. The following properties directly follows from the definition.
> 1. monotonicity: If $E_{1}, E_{2}$ are measurable sets with $E_{1} \subseteq E_{2}$, then $\mu(E_{1}) \leq \mu(E_{2}).$
> 2. continuity from below: If $E_{1} \subseteq E_{2}\subseteq \cdots$ are measurable sets that are increasing, then the union of the sets $E_{n}$ is measurable and $\mu\left( \bigcup_{i=1}^{\infty}E_{i} \right)= \lim_{i \rightarrow \infty}\mu(E_{i})= \sup_{i \geq 1}\mu(E_{i}).$
> 3. continuity from above: If $E_{1} \supseteq E_{2}\supseteq \cdots$ are measurable sets that are decreasing, then the intersection of the sets $E_{n}$ is measurable. Furthermore, if at least one of the $E_{n}$ has finite measure then $\mu\left( \bigcap_{i=1}^{\infty}E_{i} \right)= \lim_{i \rightarrow \infty}\mu(E_{i})= \inf_{i \geq 1}\mu(E_{i}).$

`\begin{proof}` `\end{proof}`




</div></div>



## Borel Sets

In real space, Borel algebra is the intersection of all [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^27dce2\|sigma-algebra]] that includes *open sets* in $\mathbb{R}$. In other words, it is the *smallest* sigma-algebra that can be defined on $\mathbb{R}$ while including all the open sets (intervals) of $\mathbb{R}$. It is useful in the sense that it only contains the necessary elements to define a measure on the set of open sets, which makes it available to define a [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^2c8d7a\|probability measure]].


>[!def] Borel sets on Euclidean space
>Let $\mathcal{F}$ be a sigma-algebra of Euclidean space $\mathbb{R}$. Then the sigma-algebra generated by the set of all intervals $\mathcal{I}$ is said to be **Borel sigma-algebra** of $$\mathcal{B}:= \bigcap\{ \mathcal{F}: \ \mathcal{I}\subset \mathcal{F} \},$$and $B\in \mathcal{B}$ is called **Borel set**.
{ #67466e}


While we defined Borel algebra under Euclidean space, it is more general to start on an arbitrary set. However, in probability theory, it is sufficient enough to define on $\mathbb{R}$, as it consists of all open and closed sets that can be defined on $\mathbb{R}$. 


>[!exm] example of Borel set
>Based on the closure properties of the $\sigma-$field, most of the familiar sets in $\mathbb{R}$ belongs to $\mathcal{B}$:
> - By construction, all *intervals* in $\mathbb{R}$ belongs to $\mathcal{B}$.
> - Since $\mathcal{B}$ is a $\sigma-$field, and as the all open sets are the countable union of intervals, every *open sets* in $\mathbb{R}$ belongs to $\mathcal{B}$.
> - Since each countable sets are a countable union of closed intervals in $\mathbb{R}$, every *countable sets* belongs to $\mathcal{B}$. In particular, $\mathbb{N}$ and $\mathbb{Q}$ are Borel sets.
> - As a $\sigma-$field, $\mathcal{B}$ includes the complement of a Borel sets, which means, the *set of irrational numbers* and the *finite sets* are also Borel sets.

## Random Variable

>[!def] random variable
>Let $(\Omega, \mathcal{F}, P)$ be a probability space. A function $X: \Omega \rightarrow \mathbb{R}$ is a **random variable** if $$\forall \alpha \in \mathbb{R}, \quad X^{-1}([\alpha, \infty))= \{\omega \in \Omega: \ X(\omega)\geq \alpha\} \in \mathcal{F}.$$Or, equivalently, we can define as $$X^{-1}(B)\in \mathcal{F}, \quad \forall B \in \mathcal{B}(\mathbb{R}),$$where $\mathcal{B}$ denotes a Borel algebra.
{ #f8eea7}


Note that the equivalence in [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^f8eea7\|#^f8eea7]] holds by the properties of [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^67466e\|#^67466e]]. Random variable is a mapping that maps each elements in the sample space $\Omega$ into a real space, which makes it available to use inequalities. Also, it restricts the sigma-field $\mathcal{F}$ to the inverse image of the Borel sets, restraining the excessive abstractness of the sample space. 

Remark that by the definition, $X$ is a ($\mathcal{F}-$)measurable function. Moreover, if $\Omega=\mathcal{B}$, then $X: \mathbb{R} \rightarrow \mathbb{R}$ becomes a Borel function, since we have $\mathcal{F}=\mathcal{B}(\mathbb{R})$.

For your information, to generalize the definition into the multivariate random variable, we can simply define $X: \Omega \rightarrow \mathbb{R}^{p}$ such that $$\forall B \in \mathcal{B}(\mathbb{R}^{p}), \quad X^{-1}(B) \in \mathcal{F}.$$

>[!def] sigma-fields generated by random variable
>Let $(\Omega, \mathcal{F}, P)$ be a probability space and let $X: \Omega \rightarrow \mathbb{R}$ be a random variable. Then a $\sigma-$field defined as $$\mathcal{F}_{X}:= X^{-1}(\mathcal{B})= \{S \subset \mathcal{F}: \ \exists B \in \mathcal{B}, \ \ S = X^{-1}(B) \} \subset \mathcal{F},$$is said to be a $\sigma-$field generated by $X$. 


# Probability Distribution

## Probability Distribution

>[!def] probability distribution
>Let $(\Omega, \mathcal{F}, P)$ be a probability space, and let $X: \Omega \rightarrow \mathbb{R}$ be random variable. Then a measure $P_{X}$ is said to be **probability distribution** of $X$ if $$P_{X}(B):= P(X^{-1}(B)).$$
{ #f02a69}


>[!prp] countably additive of probability distribution
>The set function $P_{X}$ is countably additive.

`\begin{proof}`Let $B_{i}$ are the pairwise disjoint Borel sets, then their inverse image $X^{-1}(B_{i})$ are also pairwise disjoint. By [[Mathematical Appendix/Measure Theory/Measure#^d2709d\|Measure#^d2709d]], we have $$X^{-1}\left( \bigcup_{i}B_{i} \right) = \bigcup_{i}X^{-1}(B_{i}).$$Thus by [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^f02a69\|#^f02a69]], we have $$\begin{align} P_{X}\left(\bigcup_{i}B_{i}\right) &= P\left( X^{-1}\left( \bigcup_{i}B_{i} \right) \right) \\ &= P\left( \bigcup_{i} X^{-1}\left( B_{i} \right) \right) \\ &= \sum_{i}P\big(X^{-1}(B_{i})\big) \\ &= \sum_{i}P_X (B_{i}), \end{align}$$where the third equality holds by [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^58f06f\|#^58f06f]], as $P$ denotes a probability measure. `\end{proof}`


Thus, $(\mathbb{R}, \mathcal{B}, P_{X})$ is also a probability space. Note that $P_{X}(\mathbb{R})=P(\Omega)=1$.


Using [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^f02a69\|#^f02a69]], we can re-define the independence of the random variable using measure theory.


>[!def] independence of random variable
>Let $(\Omega, \mathcal{F}, P)$ be a probability space, and let $X, Y: \Omega \rightarrow \mathbb{R}$ be random variables. We say $X$ and $Y$ are independence if we have $$\forall B_{1}, B_{2} \in \mathcal{B}(\mathbb{R}), \quad P\big(X^{-1}(B_{1})\cap Y^{-1}(B_{2}) \big) = P\big(X^{-1}(B_{1})\big) P\big(Y^{-1}(B_{2})\big).$$ 

Note that the independence between $X$ and $Y$ is equivalent to the followings.


>[!thm] equivalent of independence
>The following conditions are equivalent.
>- The random variable $X$ and $Y$ are independence. i.e. $$\forall B_{1}, B_{2} \in \mathcal{B}(\mathbb{R}), \quad P\big(X^{-1}(B_{1})\cap Y^{-1}(B_{2}) \big) = P\big(X^{-1}(B_{1})\big) P\big(Y^{-1}(B_{2})\big).$$
>- For all Borel function $f, g$, we have $$\mathbb{E}\big[f(X)g(Y) \big] = \mathbb{E}\big[f(X)\big]\mathbb{E}\big[g(Y)\big].$$
>- For the joint distribution $P$, we have $$P(X, Y)=P_{X}P_{Y}.$$

## Dirac Measure and Discrete Distribution

>[!def] Dirac measure
>Let $(\Omega, \mathcal{F}, P)$ be a probability space. Assume a random variable is a constant function: $X(\omega)=a$ for all $\omega\in \Omega$. Then its probability distribution is said to be **Dirac measure** $\delta_{a}$: $$\delta_{a}(B):= P_{X}(B) = \begin{cases} 1 & \text{if }a \in B \\ 0 & \text{if }a \not\in B. \end{cases}$$
{ #049540}


Note that the probability distribution $P_{X}$ only takes account whether the given $a$ is included in the Borel set $B\in \mathcal{B}(\mathbb{R})$ or not. This approach is fundamentally different than the one based on the difference between the discrete and continuous distribution.

>[!exm] multiple value discrete variable
Consider the case when $$X = \begin{cases} a &\text{with probability }\ p \\ b &\text{with probability }\ 1-p.\end{cases}$$Then using [[Mathematical Appendix/Probability Theory/Probability, Random Variable, and Distribution#^049540\|#^049540]], we can express its probability distribution as $$P_{X}(B)=p \delta_{a}(B)+(1-p)\delta_{b}(B).$$which means $$P_{X}(B) = \begin{cases} 1 & \text{if }a,b \in B \\ p &\text{if }a \in B \ \& \ b \not\in B \\ 1-p &\text{if }a \not\in B \ \& \ b \in B \\ 0 & \text{otherwise}. \end{cases}$$

Thus we can now define a general form of discrete probability distribution.

>[!def] discrete probability distribution
>Let $p_{i}>0$ for all $i\in \mathbb{N}$, and $\sum_{i}p_{i}=1$. Then we can express the probability distribution of a discrete random variable $X$ as $$P_{X}(B)= \sum_{i \in \mathbb{N}}p_{i} \delta_{a_{i}}(B).$$

Classical examples are:
- Geometric distribution: $p_{i}=(1-q)q^{i}$ for some $q \in (0, 1)$.
- Poisson distribution: $p_{i}= \frac{\lambda^{i}}{i!}e^{-\lambda}$.


Note that we can also define a random variable that is neither discrete nor continuous. 


>[!exm] distance between Car and B
>Suppose a car leaves city A at random between 1 pm and 2 pm. It travels at 100 km/h towards B which is 50 km from A. What is the probability distribution of the distance between the car and B at 2 pm?

`\begin{proof}`If the car starts traveling before 1.30 pm, then it can arrive at B before 2 pm. However, if it starts after 1.30, then its distance from the B would follow a uniform distribution. Thus we have $$X(t) = \begin{cases} 0 & \text{if }t \in [0, 30] \\ \left| 50 - 100 \frac{t}{60} \right| & \text{if }t \in (30, 60]. \end{cases}$$where $t$ denotes the minute when the car starts after 1 (i.e. if $t=30$, then it starts at 1.30 pm).
Then, its probability distribution can be expressed as $$P_{X}= \frac{1}{2} \delta_{0}+ \frac{1}{2} \frac{1}{50} m_{[0, 50]},$$where $m$ denotes a uniform measure. `\end{proof}`

