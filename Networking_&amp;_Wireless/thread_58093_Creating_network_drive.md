---
title: "Creating network drive?"
date: 2005-08-18
forum: Networking &amp; Wireless
---

### Post by smoshe on 2005-08-18
Just installed a second computer on my (so far) all Ubuntu network. I'm quite happy about the fact that my girlfriend is not fighting me in this effort to run all OSS all the time. 

Anyway,
I'm still reletively new to Ubuntu. This is the first serious Linux based undertaking I've ever attempted. So pardon me if I'm asking a horribly stupid question.

I have a directory on computer number 1.
I want to be able to acess it (read write) files to it from computer number 2.

Both computers are connected to the network via Linksys hardwire router.

Hostname for computer number 1 is speedy.
Hostname for computer number 2 is daffy.

I don't think I have it set up correctly.
Daffy is a base install of Ubuntu while Speedy is a base install other than the multi-media add ons I've added to it. Networking on both computers should be the same. Problem is that neither computer can see the other on the network.

Do any of you wild and crazy Ubuntu experts know of a quick fix, tutorial, or other method to make both computers see each other, and interact so that I can create a shared folder between the two machines?

Thank you for your help.

-Sam

---

### Post by nad on 2005-08-19
"I don't think I have it set up correctly."

What exactly is it that may not be correct? Are you trying to set up samba or NFS?

---

### Post by FLeiXiuS on 2005-08-19
This is not the place to ask questions, if you are new to the forums have comon sense to read the rules please.  Thank you.

*Thread Moved To Networking*

---

### Post by mikitz on 2007-11-12
This is exactly the kind of negative attitude that turns people off open source

---

### Post by weblordpepe on 2007-11-13
Anyway.

You need to use the **SSH** protocol. SSH clients are everywhere in Ubuntu, and you can access it from just the file browser.

Anyway to -share- stuff from an ubuntu box, install the **SSH daemon**. I can't remember the name of it, but search for it in ubuntu.

You can simply type like ssh://computer/folder or something. There's got to be lots of how-to guides about on this forum. It's the way to go.

---

