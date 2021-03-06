##### [19-02-14] [paper43]
-  A Simple Baseline for Bayesian Uncertainty in Deep Learning [[pdf]](https://arxiv.org/abs/1902.02476) [[code]](https://github.com/wjmaddox/swa_gaussian) [[pdf with comments]](https://github.com/fregu856/papers/blob/master/commented_pdfs/A%20Simple%20Baseline%20for%20Bayesian%20Uncertainty%20in%20Deep%20Learning.pdf)
- *Wesley Maddox, Timur Garipov, Pavel Izmailov, Dmitry Vetrov, Andrew Gordon Wilson*
- `2019-02-07`

****

### General comments on paper quality:
- Quite well-written and interesting paper. I am not quite sure how I feel about the proposed method though.

### Comments:
- It seems somewhat odd to me to first fit a Gaussian approximation to samples from the SGD trajectory and then draw new samples from this Gaussian to use for Bayesian model averaging. Why not just directly use some of those SGD samples for model averaging instead? Am I missing something here? 

- Also, in SG-MCMC we have to (essentially) add Gaussian noise to the SGD update and decay the learning rate to obtain samples from the true posterior in the infinite limit. I am thus somewhat confused by the theoretical analysis in this paper.

- I would have liked to see a comparison with basic ensembling. In section C.5 they write that SWAG usually performs somewhat worse than deep ensembles, but that this is OK since SWAG is much faster to train. "Thus SWAG will be particularly valuable when training time is limited, but inference time may not be.", when is this actually true?

- It makes intuitive sense that this method will generate parameter samples with some variance (instead of just a single point estimate) and thus also provide some kind of estimate of the model uncertainty. However, it is not really theoretically grounded in any significant way, at least not more than e.g. ensembling.

- The most interesting experiment for which they provide reliability diagrams is IMO CIFAR-10 --> STL-10. I note that even the best model still is quite significantly over-confident in this case.

- I really liked their version of reliability diagrams. Makes it easy to compare multiple methods in a single plot.
