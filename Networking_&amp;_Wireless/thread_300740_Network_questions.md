---
title: "Network questions"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Cbotron on 2006-11-16
1-How do I setup a firewall?

2-How can I navigate to other computers on my network?

3-How do I protect myself from viruse on ubuntu?

---

### Post by hearnden on 2006-11-16
1)

Try installing firestarter  ('sudo aptitude install firestarter')

2)

Yes, with different degrees of setup difficulty for different degrees of usability.

3)

I don't know if anybody really worries about viruses in Ubuntu, because there is a widespread perception that Linux is more secure anyway, and there is such little payoff for virus writers to target anything other than Windows.  You can however look at aegis-virus-scanner (there used to be one called clamscan too).

---

### Post by Jussi Kukkonen on 2006-11-16
1. There's a firewall already in the kernel, it's called netfilter. If you want a graphical user interface for it, install Firestarter from synaptic. You don't necessarily need one, though, especially if you don't run server programs.

2. There's not enough details in that question. Do you want to see (Windows) shared folders on your network or what? Have you tried *"Places --> Connect to Server..."*

3. There are very few viruses for linux. The basic advice for all operating systems stands: 
 * Do not run executables from web, e-mail
 * Do not install software from unknown sources
Most people agree that a virus scanner is is only needed if you want to prevent e.g. forwarding a Windows virus you received in an e-mail to someone else... Still, there are scanners in the repositories if you want one. Try  clamav.

---

### Post by Cbotron on 2006-11-16
thanks guys

---

