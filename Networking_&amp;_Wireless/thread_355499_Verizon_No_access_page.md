---
title: "Verizon No access page"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by ptolar on 2007-02-07
Hi everybody,
I am new to Ubunut and could definitely use some help.

It's very basic: I am trying to connect to the internet through my dsl. I have a working dsl connection in windows, but I can't get it to work under linux. Ubuntu is actually a third distro tham I am trying out, Suse and PClinuxOS didn't seem to like my hardware.

My setup is phone line connected to Westell Wirespeed dsl modem connected to the ethernet card in the computer (onboard Via VT6102). I activate the network card and run the pppoeconf to setup dsl. I get an IP and DSL servers, but when open Firefox I am always redirected to Verizon's "No access" page stating either technical difficulties or billing issue (of which it must be the former). When I called Verizon of course they tell me that as long as I have a working connection in Windows there is nothing they can help me with.

Does anyone have any thoughts? Is this a problem on my side somewhere?

Thanks a lot!

---

### Post by johnoh on 2007-03-17
Ptolar:

I'm having exactly the same experience. I'm not encouraged that no one has replied with any suggestions.

---

### Post by Jenn_RN on 2007-03-17
Hi,
    I'm a newbie too.  I'm having trouble connecting to Verizon DSL.  I also have a Westell modem connected by Ethernet.  I went to applic, access, then terminal and typed              sudo  pppoeconf       and it started to check the modem but then I got a message 'Not Connected'  and 'please check your network & modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem'  So what do I do now?

Thanks,
Jenn

---

### Post by ptolar on 2007-03-19
Well my problem has been solved. Everything works quite well. What I was doing wrong (and this is almost embarassing) was that I typed my username next to (as opossed to overwriting) the prompt in pppoeconf. So my login to Verizon's server in fact failed.

Just make sure that your ethernet card works and you should get internet.

---

