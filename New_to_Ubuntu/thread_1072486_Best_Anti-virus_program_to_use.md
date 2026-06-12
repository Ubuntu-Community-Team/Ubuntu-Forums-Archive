---
title: "Best Anti-virus program to use"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by bradthewanderer on 2009-02-17
I have a question about what is the best anti-virus program to use in Ubuntu, I have Clamtk installed but it can't install or update with new signatures, so... I was wondering if there was another program out there that is just as good, or perhaps someone could walk me through the updating of the clamtk? Thanks for any help. 

I am using the version 3.11 of clamtk.

---

### Post by donkyhotay on 2009-02-17
Unless you're configuring a headless fileserver to protect a windows computer you don't need a virus scanner on linux. If you are using linux as a desktop and "just want protection anyways" then read [this](http://www.catb.org/~esr/writings/unix-koans/nervous.html).

---

### Post by bradthewanderer on 2009-02-17
Thanks Foo.

---

### Post by Captain_tux on 2009-02-17
> **donkyhotay said:**
> Unless you're configuring a headless fileserver to protect a windows computer you don't need a virus scanner on linux. If you are using linux as a desktop and "just want protection anyways" then read [this](http://www.catb.org/~esr/writings/unix-koans/nervous.html).

Best answer I've seen to this question yet!

---

### Post by InspiredIndividual on 2009-02-17
Let me counterbalance Foo with foobar: 
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

Just so we won't become complacent... Yes, the system architecture of Linux is safer. No, that doesn't mean it's impossible to get a virus. Common sense is your best virus protector.

---

### Post by handy on 2009-02-18
> **InspiredIndividual said:**
> Let me counterbalance Foo with foobar: 
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

Just so we won't become complacent... Yes, the system architecture of Linux is safer. No, that doesn't mean it's impossible to get a virus. Common sense is your best virus protector.

So have you ever noticed a flurry of activity on these forums due to a virus or mal-ware attack?

Me either.

I use IPCop on a headless box with the Copfilter add-on, which provides the ability to run multiple anti-virus services simultaneously, which is of course due to IPCop mostly being used to protect hundreds of windows machines or servers that provide data to windows users.

I personally use ClamAV on the IPCop/Copfilter box for one reason only - it doesn't have any detrimental effect on my LAN's internet speed. :lolflag:

I don't have ClamAV running to protect our windows machines, because we don't have any. :p

---

### Post by wangsuda on 2009-02-18
> **bradthewanderer said:**
>  I have Clamtk installed but it can't install or update with new signatures, or perhaps someone could walk me through the updating of the clamtk? Thanks for any help. 

I am using the version 3.11 of clamtk.
This is an easy one! Open a terminal window (Applications>Accessories>Terminal) and paste the following code in:
```
sudo clamtk
```
Enter your password. At this point, the clamtk menue comes up. Run your update! Or you can install clamtk4.11 at [http://sourceforge.net/project/showfiles.php?group_id=131278](http://sourceforge.net/project/showfiles.php?group_id=131278)

---

### Post by rburkartjo on 2009-02-18
brad here is a link for the newest version of clamtk might want to bookmark it. new versions are out periodically./cheesemaker

[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by binbash on 2009-02-18
you have to stop apparmor if you want to update signatures at clamtk.stop apparmor, update, start apparmor

---

### Post by presence1960 on 2009-02-18
> **donkyhotay said:**
> Unless you're configuring a headless fileserver to protect a windows computer you don't need a virus scanner on linux. If you are using linux as a desktop and "just want protection anyways" then read [this](http://www.catb.org/~esr/writings/unix-koans/nervous.html).

Those Master Foo stories are great!!

---

### Post by LowSky on 2009-02-18
> **InspiredIndividual said:**
> Let me counterbalance Foo with foobar: 
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

Just so we won't become complacent... Yes, the system architecture of Linux is safer. No, that doesn't mean it's impossible to get a virus. Common sense is your best virus protector.

"please save this to your desktop and run it as a bash script...." seriously who would be that dumb

I don't use any virus protection, for a few reasons. 
1. I never ran it under Windows, and why didnt' I, well I found running a scan once a month using Malwarebytes Malware removal or PC doctor got rid of any issue I had, and there wasn't many.
I never got those pesky bugs like Antivirus 2009 or Antivirus 360..
2. You just have to be smart when visiting websites and what you download. 

3. Don't use our computer with Admin rights. In Ubuntu the smartest thing to do is to create a user account with no access to Sudo. In Windows just create a guest account. Less access means less infection.

---

### Post by InspiredIndividual on 2009-02-18
> **LowSky said:**
> "please save this to your desktop and run it as a bash script...." seriously who would be that dumb


Generally, the biggest security weakness is the user. I think that's a quite general accepted point of view. Yes, an important cause of people booting Windows getting virus infectedc is because they click something they shouldn't click. When I moved to Ubuntu, I used to believe the Linux system architecture itself was an extra barrier against such user stupidity. As shown by foobar, it's relatively easily for a virus writer to circumvene the executable bit.

I'm not telling you that you specifically need a virus protector. You're probably computer smart. The point is that the many people who get virus infected booting Windows because they click something that seems like Anna Kournikova pictures would have the same problem booting freshly installed Ubuntu. To use your words: yes, many people are indeed 'that dumb'. That's why viruses/worms/etc. are such a huge problem.

---

### Post by handy on 2009-02-18
> **InspiredIndividual said:**
> Generally, the biggest security weakness is the user. I think that's a quite general accepted point of view. Yes, an important cause of people booting Windows getting virus infectedc is because they click something they shouldn't click. 

When I had a windows support business, I used to get a large amount of work that was created by school children using the internet.

They click OK to everything.  They want every type of browser search bar, music download software, whatever FREE helpful addition they were offered.  Windows ended up looking like a wormy apple.

---

### Post by bradthewanderer on 2009-02-19
Thanks to all of you for your great wisdom and some wise-cracking :). I appreciate the help my mind is sometimes still stuck in windows mode.

---

### Post by egalvan on 2009-02-19
> **LowSky said:**
> "please save this to your desktop and run it as a bash script...." seriously who would be that dumb


Well, hold on there, pardner. :0

Some of the best boot help offered by none other than *caljohnsmith* starts out that way...

Know your sources... :KS

---

### Post by egalvan on 2009-02-19
I used to use MS Windows machines to de-louse single and networked machines.
Also to de-louse thumb-drives and USB hard-drives.

Now I use ClamAV under Linux.

So much easier. So much more peaceful.
No worries about MS-oriented nasties infecting my work machine.

ErnestG

---

