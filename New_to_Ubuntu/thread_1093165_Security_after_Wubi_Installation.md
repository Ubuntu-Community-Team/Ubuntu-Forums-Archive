---
title: "Security after Wubi Installation"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by emmwee on 2009-03-11
I read some stuff about Linux Security in this forum. Please, tell me if I understood well.
My situation: I've installed Ubuntu under Windows Vista with Wubi. All my documents are still in the original Vista directory. My PC is part of a LAN (router).
My questions:
1) If I used only Linux, I would not need neither an antivirus program nor Firewall controller for my own security. (I know: the answer is "yes")
2) If I use also Windows on my PC, everything which runs under Windows can be infected with a virus BUT *ONLY IF* I START MY COMPUTER UNDER WINDOWS USING INTERNET OR OPENING EMAILS.
3) As long as I start my pc with Ubuntu, I'm not vulnerable. EVENTUAL VIRUSES *CANNOT* ATTACK MY SYSTEM (OR THE FILES IN THE ORIGINAL VISTA DIRECTORIES) EVEN IF I READ AN INFECTED EMAIL OR OPENED AN MALICIOUS WEB SITE.
Is that true?
Thanks.

---

### Post by gn2 on 2009-03-11
I think you are correct.

One thing to remember, Ubuntu can let you copy viruses to your Windows partition(s) and will not give you any warning that you have done so.

---

### Post by skymera on 2009-03-11
Ubuntu is not affected by Windows viruses.

Unless you put one on your Windows box personally, it's pretty much safe.

Why did you choose Wubi over a seperate partition?

---

### Post by emmwee on 2009-03-11
> Why did you choose Wubi over a seperate partition?
I had some difficulties in installling Ubunto with the CD Rom, and someone in the forum said that Wubi could be a good alternative. And so I succeeded, indeed, in making Ubuntu run.

---

### Post by Mud.Knee.Havoc on 2009-03-11
You should run a firewall and stay away from malicious websites.

---

### Post by Paqman on 2009-03-11
It doesn't make any difference whether you use Wubi or the traditional install method, security considerations are exactly the same. Treat Windows and Ubuntu as completely separate systems. You'll need to take all your usual security measures in Windows. In Ubuntu you should install all the latest updates, use a strong password, stick to trusted repos, and don't install any untrusted software or run any terminal commands from an untrusted source. This should keep you well protected for a normal desktop system.

---

### Post by emmwee on 2009-03-11
Sorry - but what is a "strong" password? Should it be alphanumeric? Or should it be different from passwords used around internet forums?

---

### Post by kimikrishna on 2009-03-11
is firewall necasry for  ubuntu too ??

ok......any FREE firewall there ?

---

### Post by oldos2er on 2009-03-11
Ubuntu comes with a firewall called iptables.

---

### Post by Paqman on 2009-03-11
> **emmwee said:**
> Sorry - but what is a "strong" password? Should it be alphanumeric? Or should it be different from passwords used around internet forums?

The worst thing you can do is use a dictionary word. Best practice is a mix of upper and lower case, special characters, letters and numbers. The longer the better.

One way to make a strong password easy to remember is to use a phrase. Consider: "My son's name is Adam, and he is 12", which would be: MsniA&hi12. Easy to remember, and extremely strong.

---

### Post by Paqman on 2009-03-11
> **kimikrishna said:**
> is firewall necasry for  ubuntu too ??

ok......any FREE firewall there ?

By default, Ubuntu doesn't have it's firewall active, but it also doesn't have any services listening on ports, so there's nothing for an attacker to exploit. End result is the same.

If it makes you feel more secure, install Gufw. You can use it to inspect your configuration, and switch to a more paranoid level of security. If you install any server software you should definitely beef up the default level of security.

---

