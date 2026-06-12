---
title: "Moving House No /home"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by spillage2 on 2011-03-18
Hi All,

I have been trying to move my /home to a separate partition and have not been too successful. Ok I mean failed badly.

Running 10.04 ubuntu

I am following this how to.

[http://www.hackourlife.com/move-home-to-a-new-partition-ubuntu-10-04/](http://www.hackourlife.com/move-home-to-a-new-partition-ubuntu-10-04/)

When I get all the way to "sudo mv /home /old_home" all I get is device or resource busy.

Any help would be appreciated.

Cheers Spill the newbie...

---

### Post by vanadium on 2011-03-18
I moved my /home today without a problem. I did this from a recovery root prompt, but you could also work from a live session. Do not do that while your system is normally booted. The link does not appear to say that.

---

### Post by spillage2 on 2011-03-18
am i being a twunt .... I did this from a recovery root prompt, but you could also work from a live session..sorry dont just rub nose in it but maybe explain how to...

---

### Post by Dutch70 on 2011-03-18
It would be best to just boot to your live cd/usb to do it. Not to sound sarcastic but, I look at it like this... Trying to move it while you have it mounted (using it) is like trying to move a chair that you're sitting in. :)


> device or resource busy

Translation: Would you mind getting out of the chair so we can carry it to the living room please? lol j/k. 

Hope that works for you.

---

### Post by spillage2 on 2011-03-18
thanks dutch that what i thought...although i did get permission errors doing that..I want to do this in vmbox first so not sure if that is the issue here.

sorry all but there seems to be allot of advice out there but no real straight line talk if you know what i mean..just need clear instructions..or maybe just leave it... but i want to learn more..

---

### Post by vanadium on 2011-03-19
The instructions on the website are clear, provided you do the actions from a live CD session or a recovery prompt.

You need more explanation on running a live CD session? This is a matter of booting up with the Ubuntu installation CD. To run a recovery prompt, you need to make a selection in the grub menu, the menu that lets you choose between operating systems when you start the computer. Choose an entry that ends with "recovery mode". After that, one of the choices is "Drop to root shell prompt with networking". If you do not have the menu, then press Shift while booting to display it.

Anyway, moving your home directory isn't the most trivial thing to do. You should probably refrain from it until you are sufficiently skilled in the command line. If not, happily continue to use the system as is.

There are other, easy options to use your second partition. You could move for example your "Documents" folder, and in the current location, put a link that points to the new partition. As a user, you won't notice the change (i.e. it appears as if the documents are still in the same place).

For this to work nicely, you would need to mount your second partition permanently from /etc/fstab. We could help in that, if you want.

---

### Post by isparkes on 2011-03-19
> **spillage2 said:**
> When I get all the way to "sudo mv /home /old_home" all I get is device or resource busy.

Any help would be appreciated.

Why not copy it instead of moving it?

That way you can get a new chair, then go and sit on it and take the old chair away later when you are sure the new one is comfortable?

This means doing a couple of things:

You can change your home directory in /etc/passwd:

```
sudo vi /etc/passwd
```

and you'll see a bunch of information, Find the line that is your current user and change it to the new one you want

```
ian:x:1000:1000:ian,,,:**/home/ian**:/bin/bash
```

You can then log out and back in, and you will be using the new home dir.

Now you have two chairs. :)

---

### Post by spillage2 on 2011-03-19
Ahhh.. Ok thank vanadium now I see where your coming from. Yes I do agree that maybe I should just leave be, But once I want to do something I kinda get my blinkers on until I have got to the end.


Anyway thanks all for the input and advice..I will get there eventually and unfortunately I have the memory of a goldfish and need to be something all the time in order not to forget..must be my age.

I'm gonna try on my netbook instead of using vbox as I dont hardly use it so dont mind if I screw it up..


Cheers..Spill.

---

### Post by Dutch70 on 2011-03-19
> **isparkes said:**
> Why not copy it instead of moving it?

That way you can get a new chair, then go and sit on it and take the old chair away later when you are sure the new one is comfortable?

Now you have two chairs. :)

:lolflag: Nice!!!

---

