---
title: "Security Issues"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-03-28
Hi All,

    I was using Ubuntu for the last few months and I believe to a greater extent Ubuntu is immune(but not fully secured) to virus and hackers than windows. But I had a conversation with one of a network engineer and he said that hackers can easily hack Ubuntu  system thru any open ports, or if they can take the control of a program which executes with root previlage and take control of the system without the user knowledge. He also said that the hacking is more or less can be identified in windows environment since on most cases there will be a firewall and it will alert the users.

    How far the above facts are true? My question is even if some one hack my Ubuntu system how can i find out?

---

### Post by kanikilu on 2009-03-28
My understanding is that Ubuntu does not have any open ports by default. If you start installing servers that listen on ports like ssh (22), apache (80), webmin (10000), etc, then your exposure increases and it would be a good idea to lock down access to those ports as much as possible by using a firewall.

Check out [ufw](https://wiki.ubuntu.com/UbuntuFirewall) or [Firestarter](https://help.ubuntu.com/community/Firestarter).

For Ubuntu security in general, check out [bodhi.zazen's security thread](http://ubuntuforums.org/showthread.php?t=510812).

> He also said that the hacking is more or less can be identified in windows environment since on most cases there will be a firewall and it will alert the user Windows can be made to be pretty secure, but out of the box, I don't think it holds a candle to linux, but that's just my opinion.

Also, having been the minority linux user in a predominately windows environment at work, the main threat is not "hackers", but rather malware that either turns your machine into a zombie for a botnet, or just annoys the hell out of you with pop-ups or URL redirection, etc. That's the sort of thing you should be worried about from a network support standpoint, and as an end-user, you basically don't have to worry about that kind of stuff on linux at all, software firewall or not...

---

### Post by airtonix on 2009-03-28
he hasn't heard of firestarter?

---

### Post by binbash on 2009-03-28
what kind of network engineer is this lol.I never heard such a funny thing

---

### Post by ptn107 on 2009-03-28
kanikilu is correct.  Ubuntu ships with no open ports by default so if you're not using any server applications then you don't even need a firewall.  If you do use some server services then I recommend using ufw it's very easy to learn.

---

### Post by Chemical Imbalance on 2009-03-28
A nice gui for ufw is gufw.  
```
sudo apt-get install gufw
```
Very simple, but doesn't include things like flood protection.  I don't know if ufw allows for flood protection.  I think you have to use iptables rules for this.  Can anybody confirm this?

---

### Post by Delta28 on 2009-03-28
I don't mean this in a rude way but if your that worried about security you might want to get Arch Linux that is the highest security form of linux that I know of that is also what Dr Small runs on...If You ever heard of him...

---

### Post by InfectedWithDrew on 2009-03-28
You will not have to worry.  As a simple desktop user you will never get viruses.  You have a bigger threat from using random shell scripts than from getting targeted by a hacker.

----------------
Now playing: [Breaking Benjamin - Unknown Soldier](http://www.foxytunes.com/artist/breaking+benjamin/track/unknown+soldier)

---

### Post by hyper_ch on 2009-03-28
(1) the firewall on linux is called iptables
(2) iptables is in the kernel itself - so you got a firewall
(3) by default there are no services listening and so the firewall isn't really needed
(4) for that reason the firewall has no rules in it and lets everything pass
(5) it is also questionable if you want to to "firewall" service that you add later. If you add apache for example you normally want it to be accessible from outside - so no firewall rules needed
(6) there are good reason if you want a firewall to limit access - e.g. you install a ssh server and just want it to be avaialbe from work. in that case you would deny everything not coming from your work's IP
(7) firestarter is merely a configuration tool and if you install it, it will alter iptables without you telling first so - besides that firestarter is outdated and not officially recommended anymore. The Ubuntu devs have voted now for UFW
(8) security is not a thing you do once and then your safe - security is an ongoing process

---

### Post by binbash on 2009-03-28
> **Delta28 said:**
> I don't mean this in a rude way but if your that worried about security you might want to get Arch Linux that is the highest security form of linux that I know of that is also what Dr Small runs on...If You ever heard of him...

You don't know what you are talking about.Archlinux is just a normal distro.Not more secure than ubuntu.It is the previous step before gentoo nothing more.

---

### Post by lovinglinux on 2009-03-28
> **Jeyaganeshdj said:**
> But I had a conversation with one of a network engineer and he said that hackers can easily hack Ubuntu system thru any open ports, or if they can take the control of a program which executes with root previlage and take control of the system without the user knowledge. He also said that the hacking is more or less can be identified in windows environment since on most cases there will be a firewall and it will alert the users.


An open port doesn't pose a treat if there isn't any program listening on that port. Unlike Windows, Ubuntu has no listening applications out-of-the-box. Besides, to hack the machine, the application listening to an open port must have a security flaw to be exploited, otherwise is not a treat. If you are worried about zero day attacks (security flaws not discovered yet) you can sandbox the application listening to the open port using [AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906"). 

> **Jeyaganeshdj said:**
> ...or if they can take the control of a program which executes with root previlage and take control of the system without the user knowledge.


If someone runs a program listening to an open port as root, then he deserves to be hacked :)

> **Jeyaganeshdj said:**
> He also said that the hacking is more or less can be identified in windows environment since on most cases there will be a firewall and it will alert the users.


Seriously? I think that network manager is watching too much movies about hackers. If you want to have an intrusion detection in Linux, then read [this]("http://ubuntuforums.org/showthread.php?t=919472").

---

