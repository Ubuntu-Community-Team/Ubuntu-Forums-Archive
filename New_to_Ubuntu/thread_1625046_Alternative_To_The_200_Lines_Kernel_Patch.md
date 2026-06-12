---
title: "Alternative To The 200 Lines Kernel Patch"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by dkjMusic on 2010-11-18
Has anyone implemented the above as described at [http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html) and can testify to it significantly increasing performance for normal desktop use?

---

### Post by cariboo on 2010-11-18
I just set it up on my netbook, the system does run noticeably faster. I'd suggest you try it. If it doesn't work for you, it's pretty easy to undo the changes.

---

### Post by Joeb454 on 2010-11-18
Just tried it on my desktop - pretty hard for me to tell if it's faster, as it's a fairly powerful rig as it is. It does feel a bit snappier, but this could quite easily just be me imagining things :)

**Edit:** Just tried scrolling up and down a rather large webpage full of text, which used to lag a fair amount (I believe this is common with Nvidia cards?). Works as smoothly as you'd expect! Thanks for posting the link :)

---

### Post by mister_playboy on 2010-11-18
I tried the instructions and I get an error message every time I open gnome-terminal:

```
mkdir: cannot create directory `/dev/cgroup/cpu/user/xxxx': No such file or directory
bash: /dev/cgroup/cpu/user/xxxx/tasks: No such file or directory

```With xxxx being four various numbers

Do the lines that go in the ~/.bashrc file need to be a certain place?

---

### Post by Joeb454 on 2010-11-18
> **mister_playboy said:**
> I tried the instructions and I get an error message every time I open gnome-terminal:

```
mkdir: cannot create directory `/dev/cgroup/cpu/user/xxxx': No such file or directory
bash: /dev/cgroup/cpu/user/xxxx/tasks: No such file or directory

```With xxxx being four various numbers

Do the lines that go in the ~/.bashrc file need to be a certain place?

Try putting them at the end of the file, if you haven't already. That's where I put it on my system, and I'm not experiencing the error.

---

### Post by The Cog on 2010-11-18
> **mister_playboy said:**
> I tried the instructions and I get an error message every time I open gnome-terminal:

```
mkdir: cannot create directory `/dev/cgroup/cpu/user/xxxx': No such file or directory
bash: /dev/cgroup/cpu/user/xxxx/tasks: No such file or directory

```With xxxx being four various numbers

Do the lines that go in the ~/.bashrc file need to be a certain place?No.

The directory /dev/cgroup/cpu/user/xxxx/tasks should be created by /etc/rc.local on reboot. Check that directory exists. If not, investigate why /etc/re.local isn't creating the directory. P.S. the directory needs recreating every time it boots because it is not stored on disk - it's in virtual filesystem.

I think it feels more responsive, but I need more time to play before I'm sure.

---

### Post by drs305 on 2010-11-18
> **mister_playboy said:**
> I tried the instructions and I get an error message every time I open gnome-terminal:

```
mkdir: cannot create directory `/dev/cgroup/cpu/user/xxxx': No such file or directory
bash: /dev/cgroup/cpu/user/xxxx/tasks: No such file or directory

```With xxxx being four various numbers

Do the lines that go in the ~/.bashrc file need to be a certain place?

Did you change "user" to your username? I took them at their word and entered it just as it was posted (user).

After reading your post I substituted my username and got the error you mention.

(Yes, I know the example shows 'user')

---

### Post by Joeb454 on 2010-11-18
Based on what The Cog said - have you made /etc/rc.local executable? It sounds like it might not be running.

---

### Post by marl30 on 2010-11-18
> **mister_playboy said:**
> I tried the instructions and I get an error message every time I open gnome-terminal:

```
mkdir: cannot create directory `/dev/cgroup/cpu/user/xxxx': No such file or directory
bash: /dev/cgroup/cpu/user/xxxx/tasks: No such file or directory

```With xxxx being four various numbers

Do the lines that go in the ~/.bashrc file need to be a certain place?
I keep getting this error too. I've tried various suggested fixed but none seem to have worked.

---

### Post by mister_playboy on 2010-11-18
One of the comments left by Ricardo Ferreira on that page solved my problem (after rebooting again): > Edit your rc.local file with sudo gedit /etc/rc.local and delete the following line:
```
echo "1" > /dev/cgroup/cpu/user/notify_on_release
```

Save and exit gedit. Then, run gedit ~/.bashrc and add the following inside your if statement:
```
echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
```

So it should look like this:
```
if [ "$PS1" ] ; then
mkdir -m 0700 /dev/cgroup/cpu/user/$$
echo $$ > /dev/cgroup/cpu/user/$$/tasks
echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi
```

---

### Post by nschubach on 2010-11-18
So what's up with his warning about 64-bit?

---

### Post by mister_playboy on 2010-11-18
> **nschubach said:**
> So what's up with his warning about 64-bit?

The warning only applies to the patched kernels he has linked to... it's not a warning about following the terminal commands procedure.

The patched kernel comes with this new scheduling turned on by default... apparently the functionality has been present in the kernel for a while, but inactive.

---

### Post by libssd on 2010-11-18
Given the context described in one of the references:
> One of the problems commonly talked about in our forums and elsewhere is the poor responsiveness of the Linux desktop when dealing with significant disk activity on systems where there is insufficient RAM or the disks are slow. 
I'm not sure this change will make much difference, since I have 2 gb of RAM and a SSD, but I decided to give it a try anyway. Before I added more RAM, I did notice that as soon as swap started being used, performance fell off a cliff.

After making a fresh, restorable system backup, I made the changes and rebooted. No surprises, and no error messages. As Joeb454 says, it **seems** to be a little faster on scrolling, but that could just as easily be my imagination. But, a netbook with an N450 processor needs every bit of help it can get.

Now, can somebody explain in ENGLISH exactly **what** these changes do? I am in awe of someone like Lennart Poettering, who can rethink a 200+ line kernel patch as 5 lines of code in rc.local, but I'd like a little better understanding of how this mod actually works. The explanation here: [http://www.omgubuntu.co.uk/2010/11/linux-to-get-a-lot-faster-due-to-new-patch/](http://www.omgubuntu.co.uk/2010/11/linux-to-get-a-lot-faster-due-to-new-patch/) is gibberish to me:
> Each task&#8217;s signal struct contains an inherited pointer to a refcounted autogroup struct containing a task group pointer, the default for all tasks pointing to the init_task_group. When a task calls __proc_set_tty(), the process wide reference to the default group is dropped, a new task group is created, and the process is moved into the new task group. Children thereafter inherit this task group, and increase its refcount. On exit, a reference to the current task group is dropped when the last reference to each signal struct is dropped. The task group is destroyed when the last signal struct referencing it is freed. At runqueue selection time, If a task has no cgroup assignment, its current autogroup is used.

---

### Post by libssd on 2010-11-18
One more question: when a new kernel comes along, should this be backed out?

---

### Post by marl30 on 2010-11-18
Anybody else who was still getting an error, someone left this comment on the blog with an update that fixed the error.
> Slightly improved version of the cgroup_clean script:

#!/bin/sh
if [ "$1" != "/user" ]; then
	rmdir /dev/cgroup/cpu/$1
fi            

---

### Post by handy on 2010-11-19
I'm using this solution, which I think is an improvement to Lennart's script:

[http://lkml.org/lkml/2010/11/16/413](http://lkml.org/lkml/2010/11/16/413)

P.S. I'm running it on Arch, as is, so I expect that you will still have to use the Ubuntu specific modifications to get around the Ubuntu error message.

---

### Post by udippel on 2010-11-19
Question: is there a need to install cgroup-bin to actually make the 'hack' work??
I should think so in the first place, but could be wrong as well ...

Any expert?

---

### Post by Stigmata13 on 2010-11-21
I think I'll just wait until Canonical themselves release a patch via apt-get upgrade. As much as I love playing around with my system, its pretty stable as it is and I don't see much point in going through the risk of causing problems for myself in the future.

---

### Post by Locke_99GS on 2010-11-21
I've been running the 200 patch on a vanilla 2.6.37-rc2 kernel for about a week now on two machines. The difference is most noticeable on the older crappier machine, which is also where it's most appreciated.

Doing it outside the kernel is a kludge.

---

### Post by handy on 2010-11-21
> **Locke_99GS said:**
> ...
Doing it outside the kernel is a kludge.

Why is it a kludge?

It is so quick & easy, compared to to playing with kernels.

Initially, the only reason it is going into the kernel is to cater to the ever growing group of users that don't want to edit config files & such, which by the way, has been shown on the lkml site to give faster performance than the kernel patch. (kludge? :p)


The other thing, which is already happening (since [**_PATCH v4_**]("http://lkml.org/lkml/2010/11/20/91")), is that there are more changes in-store for us before (& after) the patch makes it into the stable kernel. 

How many of these will come to us via the easy file editing option remains to be seen.

---

### Post by leclerc65 on 2010-11-21
Yep, it works for me.
After making the patch on my desktop I made the following test: Started a download , then played a Youtube at the same time. The Youtube played smoothly up to the end, which was not the case in the old days (I don't have a very good DSL line).

---

### Post by libssd on 2010-11-22
Not only is this approach less disruptive and easier to do than building a custom kernel, according to Markus Trippelsdorf's testing, it's also significantly faster than the kernel approach (at this stage of its development): [http://lkml.org/lkml/2010/11/16/392](http://lkml.org/lkml/2010/11/16/392)

---

### Post by zsazso on 2010-11-23
First time I ever did anything even slightly complicated in terminal, and boy am I glad I did! This dinosaur is running like a much newer machine. Everything is notably faster. Especially scrolling. Multitasking no longer a dream (or nightmare).

---

### Post by libssd on 2010-11-23
Congratulations. I don't understand why some people are so unwilling to try this. As tweaks go, it's quite simple and well documented, and (in my little understanding of exactly how it actually works) very low risk, as well as much less work than building/installing a new kernel.

---

### Post by Ric_NYC on 2010-11-24
**Script To _Automatically_ Apply the "200 Lines Kernel Patch" Alternative In Ubuntu**


[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

---

### Post by dkjMusic on 2010-11-25
> **Ric_NYC said:**
> **Script To _Automatically_ Apply the "200 Lines Kernel Patch" Alternative In Ubuntu**


[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

Excellent.

BTW, did you notice the "conversation" in the ensuing comments:

Does this patch speed up all apps, or only those launched from the terminal?

**Only for the terminal. So you could create a small startup script for say Firefox and it would use this.**

**Here's how the script to launch Firefox should look like:**

**----------------**
**#!/bin/bash**
**mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1**
**echo $$ > /dev/cgroup/cpu/user/$$/tasks**
**echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release**
**firefox**
**----------------------**

**You can replace "firefox" with any application you want in the script above.**

So are such terminal-launchers the key to performance gains for sluggish apps?

---

### Post by libssd on 2010-11-25
> **dkjMusic said:**
> Does this patch speed up all apps, or only those launched from the terminal?
As far as I can see, this speeds up anything that involves I/O. Scrolling in gedit, OO3, web browser, page loads in a web browser, Nautilus performance, and video playback -- in all of which I have noticed improvements. Since the alternative patch can be disabled easily, it's not hard to do A/B comparisons. I suspect that the slower the machine, the more noticeable the differences, especially for machines with limited memory and a slow bus.

---

### Post by 1roxtar on 2010-11-30
I, personally, noticed a huge improvement with online video playback.  Video is smoother and faster.  I used to have to choose the slower resolutions because HD viewing was slow and choppy.  Now I get smooth 720HD and 1080p playback even with slower connections.   Now I can completely do away with Win7 on virtualbox and dual-boot.

---

### Post by Paddy Landau on 2010-12-01
> **udippel said:**
> Question: is there a need to install cgroup-bin to actually make the 'hack' work?
No. I installed it as an experiment, and after that I couldn't log in! I had to use recovery mode to uninstall cgroup-bin.

> **libssd said:**
> ... when a new kernel comes along, should this be backed out?
No one has answered this, and I'd like to know too, so I'm "bumping" it.

---

### Post by tobydeemer on 2010-12-01
Hi everyone-

I had implemented the WebUpd8 patch about a week ago, and everything was running great. I applied available updates today, including a kernel patch.

At first I got this error when opening a gnome terminal:
mkdir: cannot create directory `/dev/cgroup/cpu/user/xxxx': No such file or directory bash: /dev/cgroup/cpu/user/xxxx/tasks: No such file or .etc...

I then went back and applied the updated version on WebUpd8. I am now getting this error every time I open a gnome terminal window:
bash: /dev/cgroup/cpu/user/notify_on_release: Permission denied

Obviously a permissions issue, but how do I correct that? Any thoughts from more kernel savvy ones than I? Ideas appreciated. 

Also, +1 to the question of backing out these changes after newer kernels are pushed down from Ubuntu updates.

Thanks.

---

### Post by tobydeemer on 2010-12-01
Also, just realized I really need to update my sig...

Not running 9.10 anymore...

10.04.1 LTS w/ 2.6.32-26-server #48-Ubuntu SMP

---

### Post by Paddy Landau on 2010-12-02
> **tobydeemer said:**
> I then went back and applied the updated version on WebUpd8...
I don't have this problem. I suggest that you go back and carefully double-check every single change.

---

### Post by tobydeemer on 2010-12-02
> **Paddy Landau said:**
> I don't have this problem. I suggest that you go back and carefully double-check every single change.

Well, turns out you're right. I had added the changes manually to the different sections, and thought I had caught everything. I had a couple of small typos....

So I directly copied / pasted this time, and presto. 

Sheesh.


Thanks though.

---

### Post by libssd on 2010-12-02
> **tobydeemer said:**
> Well, turns out you're right. I had added the changes manually to the different sections, and thought I had caught everything. I had a couple of small typos....

So I directly copied / pasted this time, and presto. 

Sheesh.


Thanks though.
With code as opaque as this, cut & paste is the way to go.

I rarely see the name "Deemer" anywhere. There aren't many of us.

---

### Post by geoffree on 2011-01-23
How to disable the alternative patch?  I believe it's causing display problems.

Thanks,  Geoffree

---

### Post by libssd on 2011-01-23
> **geoffree said:**
> How to disable the alternative patch?  I believe it's causing display problems.

Thanks,  Geoffree

Just reverse the steps you took to enable it, then reboot.

---

### Post by afrodeity on 2011-06-09
When removing the patch, do I just comment out in bashrc, or must I remove the new folders?

---

### Post by udippel on 2011-06-09
> **afrodeity said:**
> When removing the patch, do I just comment out in bashrc, or must I remove the new folders?

I was too lazy to search for the complete set of instructions. Though I remember that stuff was added to /etc/rc.local. That's the most relevant part and has to go. The empty directories lying around are just an eyesore. 
So bring back the original rc.local-version (usually doing nothing), bring back the original .bashrc, and reboot.

---

### Post by libssd on 2011-06-09
I haven't followed this topic in some time, primarily because the patch was utterly transparent and has worked flawlessly. Am I correct to assume that this functionality has been backported to Ubuntu 10.04LTS/kernel 2.6.32-31? If so, the two co-exist.

Replying to afrodeity (interesting handle), here are my change notes for applying the patch; to disable it, just undo these changes:

______________________________________________________________________

To use Lennart's solution in Ubuntu, add the following commands in your /etc/rc.local 
(open it with: sudo gedit /etc/rc.local) file, above the "exit 0" line:

mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

If necessary, make rc.local executable:
sudo chmod +x /etc/rc.local

2. gedit ~/.bashrc
Add the following lines to the end of  ~/.bashrc:

if [ "$PS1" ] ; then 
mkdir -m 0700 /dev/cgroup/cpu/user/$$
echo $$ > /dev/cgroup/cpu/user/$$/tasks
echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

3. sudo gedit /usr/local/sbin/cgroup_clean
(Creates a new, empty file). Add these four lines:

#!/bin/sh
if [ "$1" != "/user" ]; then
rmdir /dev/cgroup/cpu/$1
fi

Then save the file and make it executable:
sudo chmod +x /usr/local/sbin/cgroup_clean

4. Restart the computer.

---

