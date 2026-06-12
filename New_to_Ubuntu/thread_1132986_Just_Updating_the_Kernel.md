---
title: "Just Updating the Kernel?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-22
I have about 260MB in updates that need downloaded, but can't get them just yet due to limited bandwidth (mobile broadband. :().

Would it be a good idea to just get the latest kernel? If so, how do I *just* update the kernel and nothing else?

I'll work on getting the other updates in the next week or two if I can spare the bandwidth (slowly, so that it's not just some massive bandwidth drain in one day)

How do I do this?

---

### Post by snowpine on 2009-04-22
I believe

```
sudo apt-get update
sudo apt-get install linux-generic
```

will install the latest kernel. (Obviously if you don't use the generic kernel, substitute the correct one.)

---

### Post by egalvan on 2009-04-22
I don't know if it will restrict the downloads to just the kernel,
but you can restrict it to just "important security updates"

Open Synaptic,
click on "Settings" tab
click on "Updates" tab

Choose only " Important security updates "
at the top part of the tab.

Close tab, then "Reload".

ErnestG

---

### Post by Noise... on 2009-04-22
> **egalvan said:**
> I don't know if it will restrict the downloads to just the kernel,
but you can restrict it to just "important security updates"

Open Synaptic,
click on "Settings" tab
click on "Updates" tab

Choose only " Important security updates "
at the top part of the tab.

Close tab, then "Reload".

ErnestG

I don't have that option in synaptic. I'm on an outdated version of Ubuntu Studio, so maybe that's the issue?

What packages would I install from update manager?

---

### Post by snowpine on 2009-04-22
> **Noise... said:**
> I don't have that option in synaptic. I'm on an outdated version of Ubuntu Studio, so maybe that's the issue?

What packages would I install from update manager?

Assuming you are using the real time kernel with Ubuntu Studio, try (from the terminal):

```
sudo apt-get update
sudo apt-get install linux-rt
```

---

### Post by Noise... on 2009-04-22
> **snowpine said:**
> Assuming you are using the real time kernel with Ubuntu Studio, try (from the terminal):

```
sudo apt-get update
sudo apt-get install linux-rt
```

How can I check what kernel I'm using?

---

### Post by snowpine on 2009-04-22
> **Noise... said:**
> How can I check what kernel I'm using?

From the terminal:
```
uname -r
```

But just to play devil's advocate... if you don't know which kernel you are using... how do you know you need to update it? :)

---

### Post by egalvan on 2009-04-22
> **Noise... said:**
> I don't have that option in synaptic.** I'm on an outdated version of Ubuntu Studio,** so maybe that's the issue?

What packages would I install from update manager?

What version are you running?

What kernel are you running 

for the kernel info, open a terminal, type this
```
uname -a
```

then copy and paste the results here.

ErnestG

---

### Post by Noise... on 2009-04-22
> **snowpine said:**
> From the terminal:
```
uname -r
```

But just to play devil's advocate... if you don't know which kernel you are using... how do you know you need to update it? :)

I know it's outdated, and that newer kernels will be more efficient. The version of 8.04 that I installed was downloaded quite a while ago, so I know that the kernel isn't the latest. 

Plus the 250MB of updates I have waiting kind of tipped me off. :P

Here's the output of uname -a

```
uname -a
Linux ubuntu 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

```

---

### Post by snowpine on 2009-04-22
The Ubuntu site tells me the latest linux-rt kernel for Hardy is 2.6.24.23.25, so there should be an update waiting for you. Use the command in my post #5.

---

### Post by egalvan on 2009-04-22
> **Noise... said:**
> I know it's outdated, and that newer kernels will be more efficient. The version of[COLOR="Red"] 8.04[/COLOR] that I installed was downloaded quite a while ago, so I know that the kernel isn't the latest. 

Here's the output of uname -a

```
uname -a
Linux ubuntu 2.6.24-19-[COLOR="Red"]rt[/COLOR] #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

```

Hardy 8.04 is LTS ( Long Term Support )
nothing "outdated" about it.
It will be supported for three years for Desktop
and five years for Server.

Also, that is a "real-time" kernel, needed for good audio work.


The way I look at it is this...

does it work well for you?
then why upgrade?

Many folks (like me :) ) prefer the stability of LTS over the "newness" of more recent releases.


As for you not having the option to only get security update,
I don't understand why not.

I have a bone-stock install of Hardy 8.04, and it shows the option,
both under Synaptic, and under Software Sources.

Can you open Software Source option, either Synaptic or directly,
and take a screenshot for us?

---

### Post by egalvan on 2009-04-22
> **snowpine said:**
> The Ubuntu site tells me the latest linux-rt kernel for Hardy is 2.6.24.23.25, so there should be an update waiting for you. Use the command in my post #5.

He's running Ubuntu Hardy Studio,
NOT a standard Hardy.
Updating the kernel willy-nilly could possibly break his system.

Of course, it could be among the 240-odd-megabytes waiting for him :)

My suggestion is he take the time to read the list of updates and see if there is a kernel update.

I'm puzzled that he has no "security only" option in Sources.
I can't imagine the Ubuntu Studio developers changed Synaptic...

---

### Post by snowpine on 2009-04-22
> **egalvan said:**
> He's running Ubuntu Hardy Studio,
NOT a standard Hardy.
Updating the kernel willy-nilly could possibly break his system.

Of course, it could be among the 240-odd-megabytes waiting for him :)


How/why would upgrading to the current kernel version using apt-get possibly break the system? 

The OP's kernel is outdated, according to Ubuntu.com: [http://packages.ubuntu.com/hardy/linux-rt](http://packages.ubuntu.com/hardy/linux-rt)

I really do not understand your post...? Apt-get is not "willy-nilly;" it is our #1 tool to prevent system breakage. :)

(edit) ps In the off chance the new kernel DOES somehow break your system, you can simply boot the old kernel from GRUB and then uninstall the broken new version. It is really a zero risk proposition.

---

### Post by egalvan on 2009-04-22
```
lsb_release -a
```

will give a bit more info on what you are running.

On my Hardy machine, it shows...
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
```


note, the Studio web site states that 

Ubuntu-Studio 8.04.1 (Hardy Heron)

is the Recommended Release.

---

### Post by Noise... on 2009-04-22
Ok. The kernel is updated without issue. There's 50MB of my large amount of updates done.

My notebook seems to be running a LOT cooler than it did on the last kernel. Is the new kernel just a lot more efficient?

---

### Post by Noise... on 2009-04-22
Also, here's the screen of synaptic.

---

### Post by egalvan on 2009-04-22
> **snowpine said:**
> **How/why would upgrading to the current kernel version using apt-get possibly break the system? **

The OP's kernel is outdated, according to Ubuntu.com: [http://packages.ubuntu.com/hardy/linux-rt](http://packages.ubuntu.com/hardy/linux-rt)

I really do not understand your post...? Apt-get is not "willy-nilly;" it is our #1 tool to prevent system breakage. :)

:P
"How do I break thee?
Let me count the ways..." apologies to WShakespeare

For the same reasons that updating the kernel can break ANY Linux system...
incompatibility with installed software..

Possible incompatibility with installed software is one reason some admins do NOT update the kernel without extensive testing.
And why many folks keep at least one previous version of the kernel...
in case something does not work right after a kernel update.

How many posts have
 "I updated the kernel, now my (wifi, net, video, etc) is broken, please help"
and the solution is
 "use the previous kernel"
or
"update your broken software"...



For the same reason that distros don't always offer the latest versions... possible incompatibility with installed software.

As for "**willy-nilly**", that referred to the **action, not the tools.**
apt-get is not a panacea...
it can't check on every single piece of software for compatibility...
that falls to the software author/users.

Lordy, there are still *nix installations out there using the 2.24 series because updating to the 2.26 series will break things. :)


And I'm still wondering what is causing his system to not show the option to only get Security Updates.

Is Hardy Studio **THAT** different from a standard Hardy?

---

### Post by snowpine on 2009-04-22
Glad you got the new kernel working, and that it's running cooler. :) Did apt-get keep the previous kernel version in your GRUB so that you can boot it in case something goes wrong with the new version?

---

### Post by snowpine on 2009-04-22
> **egalvan said:**
> :P
"How do I break thee?
Let me count the ways..." apologies to WShakespeare


I hate to be argumentative... but... are you saying the 2.6.24 rt kernel in the Ubuntu Hardy Heron LTS repository is unstable and will cause system breakage?

I might argue that NOT applying the recommended update from Canonical is more dangerous...

---

### Post by Noise... on 2009-04-22
> **snowpine said:**
> Glad you got the new kernel working, and that it's running cooler. :) Did apt-get keep the previous kernel version in your GRUB so that you can boot it in case something goes wrong with the new version?

Yes - it's still there just in case.

I thought the heat thing might just be a fluke, but now, all this time later it's still just as cool. I'm surprised the kernel would make *that* big of a difference, but I guess it did.

---

### Post by egalvan on 2009-04-22
> **snowpine said:**
> Glad you got the new kernel working, ... :)
 **Did apt-get keep the previous kernel version in your GRUB so that you can boot it [COLOR="Red"]in case something goes wrong with the new version[/COLOR]?**

> **snowpine said:**
> I hate to be argumentative... but...
** are you saying the 2.6.24 rt kernel in the Ubuntu Hardy Heron LTS repository is unstable and will cause system breakage?**

I might argue that NOT applying the recommended update from Canonical is more dangerous...

The first red bold is what I am stating....
that, at times, no not always, but sometimes, updating will cause system instability.

If this was not true AT ALL as you seem to be implying, then why 
*Did apt-get keep the previous kernel version in your GRUB so that you can boot it [COLOR="Red"]in case something goes wrong with the new version[/COLOR]*?
What could go wrong?
It's official,
it's recommended by Canonical... 
What could go wrong?
Why keep a back-up?

If, as you seem to be implying, the kernel in the repository is stable, why the suspenders?
If updating is always 100% safe and stable, why the option to keep older kernels "just in case" ???

And again, this is not a standard Ubuntu distro, it's a re-spin.
Is it officially supported by Canonical?



You tell the OP to keep a back-up "in case something goes wrong"... :confused:

and you tell me that "nothing can go wrong"...  :)

---

