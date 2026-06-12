---
title: "Is There A Version of Gparted For AMD64 Architecture?"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Still Grinding Beans on 2009-04-02
I just recently completed my first install of Ubuntu. It is version 8.10 and I am running Amd64 Architecture(Unfortunately). I have been working with tovid and now realize I didnt allow enough partition space so I burned an ISO file of GParted partitioning software(latest version) to cd. I followed instructions via Ubuntu Forums and Wiki to boot from cd and I am never given the oportunity to choose any options for language or anything else. All I get is a command line with grub and a flashing cursor prompt. I went back to sourceforge and looked at the versions of Gparted and they all seem to be for i386 architecture. Is this true or am I missing something? If so is there any free GUI easy to use partitioning software I can use to add more partition space and organize partitions? Thanks for any advice offered.

---

### Post by philinux on 2009-04-02
Yep just had a look they're all i386. This should not be a problem anyway as its' a live cd.

---

### Post by presence1960 on 2009-04-02
> **Still Grinding Beans said:**
> I just recently completed my first install of Ubuntu. It is version 8.10 and I am running Amd64 Architecture(Unfortunately). I have been working with tovid and now realize I didnt allow enough partition space so I burned an ISO file of GParted partitioning software(latest version) to cd. I followed instructions via Ubuntu Forums and Wiki to boot from cd and I am never given the oportunity to choose any options for language or anything else. All I get is a command line with grub and a flashing cursor prompt. I went back to sourceforge and looked at the versions of Gparted and they all seem to be for i386 architecture. Is this true or am I missing something? If so is there any free GUI easy to use partitioning software I can use to add more partition space and organize partitions? Thanks for any advice offered.

One of the prompts is for language. It does look a little confusing. There is a 33 for English already there, but you still have to type in a number and press Enter. The list of available languages is above the prompt as are the corresponding entry numbers needed for the prompt.

Why "unfortunately" for 64bit? If you have problems check here especially the stickys for Java, Flash etc issues: [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

for a fast java browser plugin for firefox look here: [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59) Thanks to zika for this how-to!

64bit is running smoothly now and most apps available for 32 bit now have 64 bit versions in the repositories.

---

### Post by Still Grinding Beans on 2009-04-02
Thanks Philinux and Presence 1960. I will try that Presence and repost my results. Thanks once again!

---

### Post by tarps87 on 2009-04-02
> **Still Grinding Beans said:**
> 
I went back to sourceforge and looked at the versions of Gparted and they all seem to be for i386 architecture.

i386 tends to mean the same this as 32bit now and amd64 tends to mean the same this as 64bit. All you need to know is a 32bit OS will run on a 64bit architecture, a 64bit OS won't run on a 32bit architecture.

> **Still Grinding Beans said:**
> It is version 8.10 and I am running Amd64 Architecture(Unfortunately).


That certainly not a bad thing, I've never had a problem with it.

---

### Post by Still Grinding Beans on 2009-04-02
I am still getting the same result when I boot GParted from Cd. Here is everything I see.

GNU GRUB version 0.08         (My Upper And Lower MEMORY Here)

Minimal Bash-like line editing is supported.  For the first word  TAB lists possible command completions
Anywhere else TAB lists the possible completions of a device/ filename  ]

HUH? I guess this is why Im still grinding beans. Help!!

---

### Post by aeiah on 2009-04-02
that's a little strange. ive recently been using the livecd of gparted with no problems at all. perhaps they did something in the last few days and its messed up. have you considered using a previous version? or using the ubuntu livecd? (i usually prefer an up to date gparted livecd but it isnt imperative).

---

### Post by tarps87 on 2009-04-02
> **aeiah said:**
> that's a little strange. ive recently been using the livecd of gparted with no problems at all. perhaps they did something in the last few days and its messed up. have you considered using a previous version? or using the ubuntu livecd? (i usually prefer an up to date gparted livecd but it isnt imperative).

I was just going to suggest using the Ubuntu live cd :)
I can't download the gparted iso from work (I'm there a the moment) so I will try it when I get home.
Gparted is include on the Ubuntu live cd, I think under application -> accessories or system -> administration

---

### Post by Still Grinding Beans on 2009-04-02
Thank you Aeiah and Tarps for the advice on trying to utilize GParted through the Ubuntu Live. I am getting a denial saying I need Root priveleges. What do I Do?

---

### Post by Still Grinding Beans on 2009-04-02
I was able to finally install GParted using the Ubuntu live cd. I had to enable root priveleges on terminal. I just typed "Sudo gparted" Voila!! Thank you to all the replies.

---

