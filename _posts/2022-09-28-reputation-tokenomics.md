---
layout: post
cover: 'assets/images/cover_cosmos.jpg'
navigation: true
logo: 'assets/images/logo-short-white.svg'
title: Reputation-based tokenomics Why and How? 
date: 2022-09-28 10:18:00
tags: blockchain reputation
subclass: 'post tag-content tag-test'
authors: 
 - bulat
categories: bulat
---

**TLDR; Key points**:

- Reputation-based tokenomics are promising alternatives to naive tokenomics  
- Reputation does not require a strong, persistent identity
- Obsession with Sybil resistance obscures that often Sybil tolerance is good enough 


## The new kid in town: reputation-based tokenomics 

Reputation has been getting a lot of interest in the blockchain space recently. We do not mean the reputation of crypto-influencers and project founders who dump their bags on unsuspecting community members (although undeniably fascinating topic), but reputation as proper research and engineering direction. There is certainly a lot of experimentation with different conceptual and practical reputation solutions: non-transferable tokens as a form of reputation (Soulbound tokens), DAO toolboxes for the evaluation of members’ contributions (Sourcecred, Coordinape), reputation to penalize censorship and other misbehavior (relays in MEV-boost), and many more in the development. 

This increase in interest is also mixed with other assumptions and problems which pop up in discussions on reputation in the blockchain context. The first one is the topic of identity, including various kinds of identity management solutions. The second prominent topic is a persistent concern regarding ‘Sybils.’ There is also a good chance that you have read or heard more than once that: we need an ‘identity layer’ in blockchains to solve the ‘problem of Sybils.’ These are interesting questions, and even more intriguing is to consider if all these things are parts of the same big problem. It might be helpful to try and untangle reputation from the surrounding issue first.

So why this resurgence of interest in reputation mechanisms now? Probably, one of the strongest motivating factors at the moment is a growing collective realization that we have run into a hard wall of limitations for naive tokenomics. No matter how complicated the design of the token distribution mechanism is, as long as we limit the design toolbox to monetary incentives, there are always the same problems.

For one, decentralized governance based on freely tradable tokens inevitably oscillates between plutocracy and ochlocracy. Or, in blockchain terms, ‘🐋 whale economy’ and ‘🦐 shrimp economy.’ This means that either we have to contend with a few Whales (large token holders) dictating their will or rely on the wisdom of a crowd of smaller token holders, who are often unfortunately too easily impressionable ([Wonderland story](https://www.coindesk.com/tech/2022/02/01/wonderland-founder-im-here-to-fix-this-and-make-it-all-back/)).

But generally speaking, the limitation of monetary incentive mechanisms stems from the fact that they do not allow for the easy alignment of incentives. Mercenary capital does not care for the survival and sustainability of the project but only for its own survival. And yes, the greed of the markets can do wonders, but it can also easily backfire, as it keeps reliably happening with algorithmic stablecoins. Finding people who would like to contribute because they share the goals of the project and finding a way to acknowledge the merits of their contributions arguably is a more sustainable approach for collaboration in the long term. 

Against this background, reputation has an intuitive appeal of different social mechanics that are not based on simple profit-seeking. Something that can capture those kinds of participation that are based on merits and fairness. Something that we associate with cooperation, peer recognition, and social capital. Reputation, in that sense, could be considered a different type of incentive mechanism, attracting and rewarding with social recognition those who do care about specific goals and values of the project. It may seem a bit utopian, but we have some good examples of open-software projects working this way, early Wikipedia, early Linux, and even early Bitcoin.

## Reputation system is a minefield 

Of course, the downside of this intuitive appeal is that the chase for utopian cooperation can obscure some ugly sides of reputation mechanisms. In some cases, it can just be a lazy way to deal with the problem, i.e., we have misbehaving nodes in a system, so let’s slap on identity and reputation to punish them. Treating reputation like a magic box that will solve all problems leads to hilarious and deeply disturbing results. For example, ‘decentralized’ derivatives exchange asks users for biometric verification that will be ‘safely stored with our trusted partner.’ This one is more on the hilarious side, for sure. But then we also see some ‘biometric identification hardware’ solutions to prove you are a real human, purportedly developed to fight Sybil attacks in ‘open permissionless’ systems, that lean more towards a disturbing side.

Speaking of which, Sybil attacks partially explain the interest in reputation mechanisms. To be fair, Sybils are a serious problem in blockchain or any other decentralized system. However, it is not always clear if we want a reputation to prevent Sybils, or do we want to prevent Sybil attacks in order to build a reliable reputation mechanism. The answer is: it can be both. There is no single ‘Sybil attack’ but rather a general approach of creating fake participants - Sybils - in order to exploit or disrupt the system (see layers). 

Apart from locking the system to a limited number of known participants, it is indeed quite hard to solve this problem completely. The alternative is to bound the behavior of system participants by the rules of protocol, e.g., using some form of proof or accounting for ‘good’ behavior. While we are on the topic of ‘good contributions’, it is helpful to keep in mind that ‘good’ and ‘bad’ terminology should not be taken too seriously. First of all, this is an abstraction that refers to the questions if participants behave in accordance with protocol specifications. Whether these specifications reflect good behavior in a broad sense is often out of scope. 

Secondly, social appraisal and reputation are very, very context-specific and not always can be grasped by the simple formalized metrics. While it might be tempting to translate metrics that work in some context into another contribution context, they often end up being completely divorced from reality. This is not about tradeoffs but about the poor practice of applying wrong tools to wrong problems (also, this is how you get the monstrosity of social-credit scores). Finally, different contexts can provide radically different interpretations for the same contribution. Contributor to financial privacy software is worthy of high moral praise, yet sadly they can be painted by malicious entities as money launderer if they have enough power to frame these contributions in a different context. So there are very few (if any) good reasons to propose universal on-chain identity and reputation (self-cite). 

Nevertheless, reputation mechanisms can be quite useful in a specific, well-defined context. Reputation mechanisms can be used to acknowledge the merits of contributions and even organize the distribution of resources on the basis of merits. And suppose we want to have some guarantees against adversarial misuse of reputation. In that case, it should be done without centralized reputation aggregators and without strong persistent identity, such as on-chain identity. This may seem counter-intuitive at first, but a functioning reputation mechanism, in fact, does not need a strong or persistent identity mechanism. Nor do we need a strong identity to address the problem of Sybil attacks in a satisfactory manner. The breakthrough significance of Nakamoto consensus, by the way, is that it side-steps these problems so elegantly. It does not matter who you are, anyone can join and update the ledger, but the damage that participants can do is bounded. So can we have a decentralized and permissionless reputation in the same spirit?

## Decentralized Reputation

Thanks to 30 years of P2P research, we know all mechanisms to tackle Sybils, and misbehaving participants in decentralized networks have certain tradeoffs, going beyond privacy problems. These tradeoffs can be presented as a trilemma (everybody loves them, right?) or a design space where the choice of instruments limits the available space of a triangle. It is a viable representation given that most well-known reputation tools broadly fall into three categories: cryptographic proofs, trusted oracles, and social feedback.


As a general concept, cryptographic proof solutions were proposed as early as the [1980s](https://chaum.com/wp-content/uploads/2022/02/techrep.pdf)). Bounding the behavior of system participants through cryptographic proofs is a compelling concept but, unfortunately, not very generalizable when we try to use it as proof of 'good contributions'.

For instance, consider a DAO where all contributions of participants and cryptographically proven and independently verifiable for anyone; it starts looking a bit strange. For one proving in a trustless way that a contribution was made is very hard. This works only with a narrow type of resource contributions, such as proof of storage, proof of computing, proof of bandwidth and etc. The second tricky issue is that there is not always an easy way to generate, share, and agree on the proofs in a trustless way globally. 

Thus, to ensure that we account for all contributions of DAO participants in such a fashion, we need some very weird solutions. E.g., some key-logging software on a machine of a DAO participant that record all your contributions, signs them cryptographically, and uploads them to a public ledger. There are, of course, other ways to account for the 'good' and 'bad' behavior in a system that does not require such cumbersome logic. 

The use of trusted oracles also has some serious limitations. If we introduce trusted oracles to account for participants' behavior, this puts a hard limit on how permissionless the system can be. And if we try to decentralize oracles, we end up either with prediction markets, or we move in the direction of the third type of mechanism: social networks feedback. 

Social feedback or social network feedback are mechanisms where peers evaluate each others' contributions and exchange this information as a P2P network. They got initially popular with the success of social networks in Web2, and maybe also got mixed up with problems inherent to social media networks. However, social feedback mechanisms have some peculiar properties that make them worthy of a second look. These are very flexible methods that can be adapted to different types of contributions, as peers can determine the semantics of feedback themselves. DAO participants, for example, can endorse their peers for any kind of contribution. Secondly, it can be as decentralized and permissionless as we want. This information can be shared and aggregated between participants in the P2P network. 

## Sybil-Tolerance to the rescue

Of course, this leaves us with a remaining trade-off: the problem of Sybil resistance. One can create multiple accounts to boost one's reputation or boost the reputation of one's Sybils. However, one crucial point we need to consider here. Full Sybil-resistance is not something that we are really after. To think about it, Sybils are not necessarily bots. It is perfectly possible to hire real humans to act as your Sybils. This, by the way, again highlights the questionable purpose of surveillance-style 'proof of real human solutions. Or consider that it is always possible to organize off-channel collusion between different participants to achieve the same goals as Sybil attack could achieve. It is a very strong and plausible conjecture then that fully guaranteed Sybil-resistance is neither possible nor necessary in real-life decentralized systems.  

What we care about in most cases, though, is not the absence of Sybils but that attacks of these type do not break or undermine the functionality of a system. Say if the reputation mechanism is used to distribute rewards, Sybil attack will be bounded so that the attacker can get some threshold-bounds resources. This brings us to the question of Sybil-tolerance: Can our system tolerate these types of attacks? And it turns out that we can indeed design a social feedback mechanism that is Sybil-tolerant.  
Social feedback mechanisms intuitively translate well into collaboration schemas, with resource distribution based on contributions' merits. Many social arrangements have been made in the same way. So we can try to translate these principles into the context of DAO applications as well. E.g., peers can provide feedback to each other resulting in a reputation ranking that can be used to distribute rewards from DAO treasury proportionally to accrued reputation. 

However, naive approaches to account for reputation in P2P networks would not do here. For example, graph measurements based on simple global centralities, such as vertex degrees, are easily manipulable. In fact, even complex global reputation mechanisms, such as PageRank, are not Sybil tolerant. Such vulnerability trivially follows from the fact that any node in the network can gain a reputation by adding any new edge. Thus, the attacker can unboundedly gain benefits from the Sybil attack without the need to create any attack edge. 

We refer the curious reader to learn more technical details on how to make Sybil-tolerant reputation from our [paper](http://arxiv.org/abs/2207.09950). 




