---
title: "questions about the CLI"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by josephmills on 2011-03-30
Hi there I am new to ubuntu, and love it. I might not word this right but here I go. Is there a way to see all of the things that go on in the cpu? and add  filter system for that? I have only been working with ubuntu for a couple of months. So if this has been answered(which I am sure it has) I am sorry for the re-post. thank you for your time.

---

### Post by r-senior on 2011-03-30
Not exactly sure what you are looking for, but you could try:

a. System Monitor (System -> Administration -> System Monitor)

b. top

```

$ top

```

When 'top' is running, press 'h' for help. As an example, if you wanted to sort by memory usage, from the main screen hit 'F' then 'n' then <return>. If you want to sort by CPU, hit 'F' then 'k' then return.

Other things to look at would be ps:

```

$ ps -ef

```

As always, manual pages are available for these, e.g.:

```

$ man ps

```

---

### Post by josephmills on 2011-03-30
thank you r-senior this helps a ton.

---

### Post by seawolf167 on 2011-03-30
Just want to add a couple things:

You might like *htop* more than *top*, its a little easier to see/use IMO

```
sudo apt-get install htop
```

If you are looking for a specific process, don't forget you can filter the output through *grep* (or hit F3 in *htop*)

```
ps -ef | grep -i firefox
```

---

### Post by Paqman on 2011-03-30
> **josephmills said:**
> Is there a way to see all of the things that go on in the cpu?

Not in the CPU as such, but the kernel (ie: the core of the operating system software) does keep logs, check out System > Admin > System Logs.

---

### Post by josephmills on 2011-03-30
so to be a little more clear say I wanted to look at my wireless card and see how it communicates between the bus and the cpu. Is there a way to do that?Or say I wanted to see how one part of my hard drive is loaded and I just want to see what the code is that is running through the front side bus. Is there a way to do that? I understand python(kinda:)) and I also understand C C++ so I was wondering if I could see what Syntax is being passed though the compiler. I don't know if I cleared this up or made it more confusing because I really don't know all that much, but boy ohh boy do I want to learn.  thank for all of your time.

---

### Post by josephmills on 2011-03-30
> **Paqman said:**
> Not in the CPU as such, but the kernel (ie: the core of the operating system software) does keep logs, check out System > Admin > System Logs.

thank you for clearing that up. I am very new and was intimadated to even post this because I knew that I was going to word it wrong so thanks once again for clearing it  up

---

### Post by josephmills on 2011-03-30
> **seawolf167 said:**
> Just want to add a couple things:

You might like *htop* more than *top*, its a little easier to see/use IMO



What's IMO mean?

---

### Post by mastablasta on 2011-03-30
IMO = in my opinion

---

### Post by josephmills on 2011-03-30
> **mastablasta said:**
> IMO = in my opinion

thanks shows how much of a n00b I really am but now I know. I guess asking is the only way to find out. I have to let my pride go

---

### Post by Paqman on 2011-03-30
> **josephmills said:**
> thanks shows how much of a n00b I really am but now I know. I guess asking is the only way to find out. I have to let my pride go

Don't worry about it. We were all Linux noobs once. The only annoying noob is the one that won't help themselves or won't listen, and you don't come across like that at all.

---

### Post by josephmills on 2011-03-30
> **Paqman said:**
> Don't worry about it. We were all Linux noobs once. The only annoying noob is the one that won't help themselves or won't listen, and you don't come across like that at all.
thanks! I will try to be as open as possible and will always try to listen and learn

---

### Post by Megaptera on 2011-03-30
Hi josephmills,
While you're getting used to CLI you may find this useful CLI Companion (quote) "CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list."

Here: [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

