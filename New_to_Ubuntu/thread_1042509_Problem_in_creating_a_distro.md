---
title: "Problem in creating a distro*"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by codfishy on 2009-01-17
First and foremost, I would just like to say thanks.  In the past week I just installed Ubuntu and am so familiar with the interface.  I couldn't have done it without all of you people.  Thanks.

Now for the problem:  [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
I am currently trying to create my own Linux Distributon, based on Ubuntu.  Sadly enough, I can't get past the first step.  I do have squashfs-tools and genisoimage as it says that I do in Synaptic Package Manager.

I follow each of the steps clearly, without mistakes in typing it(I copy then paste it).
I do everything right.. but it tells me "No such file or directory" even though there really IS a file called that.  It's even on the desktop for crying out loud!

---

### Post by Morpheun on 2009-01-17
make sure you have it in the same folder as the rest of the things you're working with, or type out the full path (/home/*name*/Desktop/*filename*).

Although if you have Ubuntu installed already creating a custom cd seems pointless, all those configuration options can be easily made within the os itself.

---

### Post by codfishy on 2009-01-17
> **Morpheun said:**
> make sure you have it in the same folder as the rest of the things you're working with, or type out the full path (/home/*name*/Desktop/*filename*).

Although if you have Ubuntu installed already creating a custom cd seems pointless, all those configuration options can be easily made within the os itself.

Really?  I can just begin working on the distro.. itself?
Is there like a certain program I should use to help me change the entire thing.. or do I just use the terminal?  I've gotten really familiar with the terminal, but I don't know alot of those codes you put in.

---

### Post by Morpheun on 2009-01-17
well, it depends what you want to change. There are beginners guides everywhere that'll help you get started. However, most tweaks are under "System", in administration, preferences, or control center. Adding programs can be done under Applications --> Add or remove programs. Or by typing "sudo apt-get install (or remove) <name of program>"

---

### Post by talsemgeest on 2009-01-17
It might be easier for you to use [remastersys](http://www.remastersys.klikit-linux.com/).

Just customize your ubuntu installation how you want, run remastersys and it will make a custom ubuntu iso for you.

---

### Post by codfishy on 2009-01-17
> **talsemgeest said:**
> It might be easier for you to use [remastersys](http://www.remastersys.klikit-linux.com/).

Just customize your ubuntu installation how you want, run remastersys and it will make a custom ubuntu iso for you.

So basically remastersys just creates an iso of what I created. right?
so as long as I customize the way everything looks, I'm okay?

---

### Post by talsemgeest on 2009-01-17
> **codfishy said:**
> So basically remastersys just creates an iso of what I created. right?
so as long as I customize the way everything looks, I'm okay?
Yes it will. When you install, it will be exactly as it was when you created the iso.

---

### Post by codfishy on 2009-01-17
> **talsemgeest said:**
> Yes it will. When you install, it will be exactly as it was when you created the iso.

Do you know about LFS(Linux From Scratch)?
I've heard of it, and I am planning on using it.

---

### Post by talsemgeest on 2009-01-17
I don't mean any offense, but for someone who has only just started with ubuntu, I doubt you will be able to use lfs. First, you should get used to working from the command line, then move on to something like [gentoo](http://www.gentoo.org/). Once you become very competent with gentoo, then perhaps you could start learning how to create your own linux distrobution using lfs.

---

