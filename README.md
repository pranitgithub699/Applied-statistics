Here this are the assignment questions which i've solved using Python    

1. (Visualisation, 2.5 mark) You want to visually inspect if samples could have come from a Beta dis- tribution with parameters (10,12). To do this you will plot a QQ plot of the sample percentiles (of the samples) against the exact percentiles of Beta (10, 12). Do this for samples generated in the following way: start by importing from scipy.stats import uniform, beta then define
(a) samples1 = uniform.rvs(size=10000)
(b) samples2 = beta.rvs(a=3, b=12, size=10000) (c) samples3 = beta.rvs(a=11, b=3, size=10000)
From each of these three QQ plots, identify one feature of the data which does not correspond to the Beta (10, 12) model (e.g. the samples have a larger/smaller ... than the model).
 i=1
Normal(μ, σ)
1
2. (Independent sum of two probability measures, 3.5 marks) Recall from the lectures that if we have two probability measures P1 and P2 with respective densities f1 and f2, then the density of the sum1 P1 + P2 is given by the convolution of the two densities, viz.
Z∞ −∞
f1(x)f2(t − x) dx.
In this question we consider the sum of two χ2 distributions, χ2m and χ2n with m and n degrees of freedom2
f1+2(t) = respectively. We will take m = 3 and n = 5.
(a) What is the support of χ2m? What is the support of χ2n? Therefore, what is the support of χ2m +χ2n?
(b) Write a function which implements the integrand of the integral above, that is to say that implements f1(x)f2(t − x), where f1 is the density of χ2m and f2 is the density of χ2n. (Hint: (a) this function will need two arguments, (b) you can define it easily using the pdf method of the distributions in scipy.stats.chi2.)
(c) Next, generate 100 points (t1, . . . , t100) along the support of χ2m + χ2n (using numpy’s linspace function for example), and using a for loop, compute the pdf f1+2(ti) at these 100 points using scipy.integrate.quad. (Hint: the documentation of quad has an example showing how to integrate a function with two arguments along its first argument.) Plot your result.
(d) Generate 10000 samples from χ2m, 10000 samples from χ2n, add them, and plot a histogram of these sums along with the pdf computed in the previous step. What do you observe?
(e) It is known that the sum χ2m + χn is a the distribution χ2m+n. Check that this is indeed the case by plotting the pdf of χ2m+n in a new plot which you will place side-by-side with the previous plot.
3. (Sample mean distribution, 4 marks)
• Sampling from the sample mean distribution. Write a function called sample_mean_samples
taking as inputs two integers m and n. The function should return an array of length n containing
samples each obtained by taking m samples from the χ2 distribution with k = 3 degrees of freedom k
and computing their sample mean. Call
– sample_mean_samples(m=10, n=10000),
– sample_mean_samples(m=100, n=10000), and
– sample_mean_samples(m=1000, n=10000)
and plot a histogram for each of these outputs. What you are doing here is sampling from
1 Xm km∗kkk
 (χ2) ≜Avgm(χ2 ⊗...⊗χ2)=
| {z } mi=1
χ2.
• Distribution of sample means. Using Question 2, you can work out what the distribution of
m times
the sum of m χ2 distributions with k = 3 degrees of freedom is. Moreover, it is known that for any
k23 k positive number r, the distribution rχ is given by the gamma distribution Gamma α = , θ = 2r .
k2
From these two facts, explictly compute the distribution of the m-sample means (χ2) . Create a
 km
class sample_mean_distribution whose constructor takes an integer m as input and creates this distribution. (Hint: (a) think about how probability measures/distributions are concretely represented, (b) the gamma distributions can be written in several equivalent ways, make sure you’re using the correct one and that you check scipy.stats.gamma’s documentation.) Instantiate the objects
– sample_mean_distribution(10),
– sample_mean_distribution(100), and – sample_mean_distribution(1000)
and plot their PDFs.
• Compare (a) the 3 histograms, (b) the 3 PDFs and (c) the histograms with the PDF. What conclusions do you draw?
