---
title: "Upgrading Kernel in Maverick"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by mlnease on 2011-04-14
Hello,

Been having some trouble with Wine in Maverick and am advised that I need to upgrade my kernel.  Please pardon my ignorance--I did try to search the forum for this to no avail--but just how do I go about upgrading the kernel?  I've been using Ubuntu exclusively since Dapper but have never encountered exactly this issue before.  Any advice much appreciated.

Thanks in Advance,

mike

---

### Post by Dutch70 on 2011-04-14
See if using update manager as opposed to the terminal for updates finds a newer kernel.

---

### Post by rosencrantz on 2011-04-15
Try, in a terminal, apt-cache policy linux-generic 
You should get the installed version and update candidates according to the repositories you have set up (assuming your kernel is the generic one).
What version are you supposed to upgrade to? Try to find a Debian package, compiling a kernel from source is a bit ugly.
After installing the new kernel, you should have the kernel image and initrd in /boot. Run sudo update-grub for grub to include it in its configuration.
If something goes wrong, you can still use grub to boot into the old kernel, so *don't* delete or uninstall it.

---

### Post by beew on 2011-04-15
I have some recent experience :)
[URL="http://ubuntuforums.org/showthread.php?t=1726308"]
http://ubuntuforums.org/showthread.php?t=1726308[/URL]

You can find a link where you can find .deb files for the kernels and their headers. Installing them is easy and you can remove them with Synaptic if they don't work (boot into an older kernel first)

Didn't work too well with my hardware, but maybe it will work better for you.

---

### Post by Paqman on 2011-04-15
Easiest thing to do would be simply upgrade to Natty when it's released. New versions of Ubuntu always have an updated kernel.

Was there a specific kernel version you were told you would need?

---

### Post by mlnease on 2011-04-15
> **Dutch70 said:**
> See if using update manager as opposed to the terminal for updates finds a newer kernel.
Hi Dutch70 and thanks for the quick response but no, update manager finds the same kernel ( 2.6.35.28.36 ).

---

### Post by mlnease on 2011-04-15
> **rosencrantz said:**
> Try, in a terminal, apt-cache policy linux-generic 
You should get the installed version and update candidates according to the repositories you have set up (assuming your kernel is the generic one).
What version are you supposed to upgrade to? Try to find a Debian package, compiling a kernel from source is a bit ugly.
After installing the new kernel, you should have the kernel image and initrd in /boot. Run sudo update-grub for grub to include it in its configuration.
If something goes wrong, you can still use grub to boot into the old kernel, so *don't* delete or uninstall it.

Thanks, Rosencrantz, here's the output: ```
mn@mn-OptiPlex-745:~$ apt-cache policy linux-generic 
linux-generic:
  Installed: 2.6.35.28.36
  Candidate: 2.6.35.28.36
  Version table:
 *** 2.6.35.28.36 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick-security/main i386 Packages
        100 /var/lib/dpkg/status
     2.6.35.22.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
mn@mn-OptiPlex-745:~$ 
```The advice to upgrade didn't specify a kernel.

I've never compiled a kernel, so yes, a Debian package would be ideal.  Should I just look for any higher version than mine and install it with gdebi?  Or...?

Thanks again, all, for the responses.

mike

---

### Post by KegHead on 2011-04-15
Hi!

The easiest way:

sudo apt-get update

sudo aptitude install linux-image -f

KegHead

---

### Post by jcolyn on 2011-04-15
Here's the easiest way to upgrade to the very latest kernel. Click the link This is on the Linux Mint forum. [http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=kernel](http://forums.linuxmint.com/viewtopic.php?f=42&t=40185&hilit=kernel)

Kendall I one of the Linux Mint developers and explains it well..

---

### Post by KegHead on 2011-04-15
Hi jcolyn,

Your method is great for an experienced user who can select the kernel they want.

To be safe I'd go the terminal route!

Just my 3 cents!  (inflation)

KegHead

---

### Post by mlnease on 2011-04-15
Thanks, KegHead and Jcolyn!  I'll give these a try as soon as I've finished a big update and post my results.

Gotta love this forum.

---

### Post by KegHead on 2011-04-15
Hi!

Let us know how it goes!

KegHead

---

### Post by mlnease on 2011-04-15
> **KegHead said:**
> Hi!

The easiest way:

sudo apt-get update

sudo aptitude install linux-image -f

KegHead
Hello Again, KegHead,
I ran the above code and my kernel remains the same.  
```
mn@mn-OptiPlex-745:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 2.6.35.28.36
  Candidate: 2.6.35.28.36
  Version table:
 *** 2.6.35.28.36 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick-security/main i386 Packages
        500 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.6.35.22.23 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
mn@mn-OptiPlex-745:~$
```I assume that's because this is the only Maverick candidate?

On the other hand, I no longer seem to be receiving the Wine error message so...thanks again!

---

### Post by KegHead on 2011-04-15
Hi!

You ran;

 apt-cache policy linux-generic

try:

sudo apt-get update

sudo aptitude install linux-image -f

You'll be asked to restart..do so.

Please post you result.

KegHead

---

### Post by mlnease on 2011-04-15
> **KegHead said:**
> Hi!

You ran;

 apt-cache policy linux-generic

try:

sudo apt-get update

sudo aptitude install linux-image -f

You'll be asked to restart..do so.

Please post you result.

KegHead
Hello Again,

Actually, I *did* run 
```
sudo apt-get update

sudo aptitude install linux-image -f

```*first*--but I'm not sure that I restarted.

After that I ran
```
apt-cache policy linux-generic
```to see if the kernel had changed.  It hadn't but maybe that's because I failed to restart.

I'll restart and get back with the results--sorry for the confusion.

---

### Post by mlnease on 2011-04-15
Well, now!

I tried KegHead's solution twice and Jcolyn's once--thanks very much to you both.

KegHead's had no effect on my existing kernel.  Jcolyn's interesting Mint link worded fine--I more or less successfully upgraded to 2.6.37--but wine still didn't work and neither did my wireless connection.  Couldn't seem to get to the bottom of the wireless problem and, since my problem wasn't solved, I used Synaptic to uninstall the new kernel and updated grub2--so now I'm back where I started, which really isn't so bad.

I can still use wine in Lucid (I multi-boot, if I haven't mentioned it) and the whole process has been educational.

I'd particularly like to thank you, KegHead, for your caveat about "...great for an experienced user who can select the kernel they want..."--which was *very* apt in my case; and you, Jcolyn, for encouraging me to expand my skills a little.  Doing so via the Mint link was interesting even though ultimately unproductive.

At this point I think I'll just wait for Maverick to catch up to the wine problem (there are many others out there attempting to address this) and just switch to Lucid when I want to use wine.

So I'm giving up on this for now; please let me know if you think I should therefore mark this thread SOLVED.

Thanks Again,

mike

---

### Post by rosencrantz on 2011-04-15
Yes, the apt-cache policy was only to see what's available. If the available candidate isn't more recent than what you have installed, updating with apt-get alone isn't going to help, you'll either need additional repositories, kernel .deb files or the source package (in order of increasing installation complexity).

I agree waiting is probably going to help, as the Natty release is just in two weeks. Maybe they'll treat Maverick to a kernel update to mark the occasion - or you can just do the distribution upgrade.

Edit: Natty Beta (I have it on VBox) runs on 2.6.38-7. And better don't mark it before you find a kernel that works.

---

### Post by mlnease on 2011-04-15
> **rosencrantz said:**
> Yes, the apt-cache policy was only to see what's available. If the available candidate isn't more recent than what you have installed, updating with apt-get alone isn't going to help, you'll either need additional repositories, kernel .deb files or the source package (in order of increasing installation complexity).

I agree waiting is probably going to help, as the Natty release is just in two weeks. Maybe they'll treat Maverick to a kernel update to mark the occasion - or you can just do the distribution upgrade.

Edit: Natty Beta (I have it on VBox) runs on 2.6.38-7. And better don't mark it before you find a kernel that works.
Well, I've certainly enjoyed Maverick--guess I'll take the plunge with Natty and see what happens.

Thanks again, All.

---

