---
title: "Ubuntu can't see shared folders of windows 7"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by oleg8 on 2014-02-23
Hello. There are two computers. One with Windows 7, second with ubuntu 12. Computers are connected via a router to the network and to the Internet. Computer with ubuntu 12 is connected via Wi-fi. The problem is that ubuntu 12 does not see the shared folder of Windows. The Windows is configured correctly, since android (es exployer) tablet use of windows shared folders. How to configure ubuntu, that it can use  windows shared folders.

---

### Post by squakie on 2014-02-23
Same workgroup?

---

### Post by oleg8 on 2014-02-24
> **squakie said:**
> Same workgroup? Yes, they are same: "WORKGROUP". I use Nautilus. I think it has to show all computers, which be in the network. But it doesn't.

---

### Post by Bucky Ball on 2014-02-24
So you obviously have Samba installed in Ubuntu. Maybe a silly question but best to check ...

---

### Post by bab1 on 2014-02-24
> **oleg8 said:**
> Yes, they are same: "WORKGROUP". I use Nautilus. I think it has to show all computers, which be in the network. But it doesn't.

What do you get when you use Nautilus like this:  Cntl+l >> network:///

That should show the Computers in the default WORKGROUP and the 'Windows Network" icon.  What happens it you click on the "Windows Network" icon?

---

### Post by sandyd on 2014-02-24
> **oleg8 said:**
> Hello. There are two computers. One with Windows 7, second with ubuntu 12. Computers are connected via a router to the network and to the Internet. Computer with ubuntu 12 is connected via Wi-fi. The problem is that ubuntu 12 does not see the shared folder of Windows. The Windows is configured correctly, since android (es exployer) tablet use of windows shared folders. How to configure ubuntu, that it can use  windows shared folders.

Are you using windows homegroups by any chance - samba doesnt support them

---

### Post by oleg8 on 2014-02-24
> **Bucky Ball said:**
> So you obviously have Samba installed in Ubuntu.

Yes. I have installed the Samba.


> **Bucky Ball said:**
> Maybe a silly question but best to check ...

I think this question is not silly because I am beginner to using  the Ubuntu

---

### Post by oleg8 on 2014-02-24
> **bab1 said:**
> What do you get when you use Nautilus like this:  Cntl+l >> network:///

That should show the Computers in the default WORKGROUP and the 'Windows Network" icon.  What happens it you click on the "Windows Network" icon?

When I use network:/// Nautilus shows 'Windows Network' icon only. There is nothing when I click on the "Windows Network" icon

> **sandyd said:**
> Are you using windows homegroups by any chance - samba doesnt support them

Sorry. I don't understand

---

### Post by bab1 on 2014-02-24
> **oleg8 said:**
> When I use network:/// Nautilus shows 'Windows Network' icon only. There is nothing when I click on the "Windows Network" icon


Post the output of this terminal command```
smbtree -d3
```...don't be surprised.  There may be a lot of output.  Just copy and paste it between the code blocks using the [SIZE=4]#[/SIZE] icon at the top (in the center) of the advanced editor formating icons.

---

### Post by oleg8 on 2014-02-24
> **bab1 said:**
> Post the output of this terminal command```
smbtree -d3
```...don't be surprised.  There may be a lot of output.  Just copy and paste it between the code blocks using the [SIZE=4]#[/SIZE] icon at the top (in the center) of the advanced editor formating icons.

I copy output of terminal command```
smbtree -d3
```. But I don't understand where I have to paste it. What's you mean " the advanced editor formating icons". May be it is stupid question. But I am just beginner.

---

### Post by bab1 on 2014-02-24
> **oleg8 said:**
> I copy output of terminal command```
smbtree -d3
```. But I don't understand where I have to paste it. What's you mean " the advanced editor formating icons". May be it is stupid question. But I am just beginner.

When you are replying to me you are using the editor.  In the advanced mode there are a series of formatting icons at the top.  Look for the one that is the [SIZE=4]# [/SIZE]icon.  Click on that and past the information in the editor between the code blocks and send it to me.

---

### Post by lucasdolis on 2014-04-20
Hi,

I have the same sharing issue but on Windows 8.
I have a Dell notebook which network adapter has stopped working. I thought that using linux should solve part of the problem and i was right. Using a liveUSB with Ubuntu 13.10 the network adapter works just fine.
I want to backup the files to another PC with Windows, with enough space, but i could not set up samba to share the files properly. This PC sees the folders but cannot access them.

I also tried to run ubuntu via liveUSB on both notebook and PC, but they could not even see each other.

Is there a way to solve this?

---

### Post by bab1 on 2014-04-20
> **lucasdolis said:**
> Hi,

I have the same sharing issue but on Windows 8.
I have a Dell notebook which network adapter has stopped working. I thought that using linux should solve part of the problem and i was right. Using a liveUSB with Ubuntu 13.10 the network adapter works just fine.
I want to backup the files to another PC with Windows, with enough space, but i could not set up samba to share the files properly. This PC sees the folders but cannot access them.

I also tried to run ubuntu via liveUSB on both notebook and PC, but they could not even see each other.

Is there a way to solve this?
If you can't share with a Windows to Windows situation I doubt that Samba will help you.  Samba is an Open Source application that works just like Windows sharing.

I won't be able to help you much with your Windows to Windows problem, but I am curious about it.  What is not working with Windows sharing?

---

