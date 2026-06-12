---
title: "How  do I set up my television as my primary monitor?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Antedeluvian on 2009-08-31
Definitely a newbie. I have Ubuntu 8.04 running. I  had an GeForce 6200 NVIDIA card installed today. I want to stream news shows like from MSNBC through my computer to my television. Currently I use my computer monitor side by side to my television.  I will use svideo cable to make the connection. Where do I start?

---

### Post by zipperback on 2009-08-31
Plug in the svideo cable from your computer to your svideo input, boot up your computer, it should recognize that you have your svideo device connected.

You can check to see if it sees the svideo monitor by going to the following:

System -> Preferences -> Display

Click detect monitors. And there you go.

- zipperback
:popcorn:

---

### Post by Antedeluvian on 2009-08-31
I do not see"Display" after I click preferences. Is there another term which has replaced Display?

---

### Post by PGScooter on 2009-09-01
I see Display. Are you sure you're running Ubuntu? Which version?

---

### Post by Paqman on 2009-09-01
> **Antedeluvian said:**
> I do not see"Display" after I click preferences. Is there another term which has replaced Display?

If you've got the Nvidia drivers installed you should have an Nvidia settings tool in your System menu that can be used to detect and set up the TV.

---

### Post by Antedeluvian on 2009-09-02
> **PGScooter said:**
> I see Display. Are you sure you're running Ubuntu? Which version?
I am running Ubuntu 8.04. I have searched and cannot find DISPLAY so any compass you can send me will help.

---

### Post by Antedeluvian on 2009-09-02
> **Paqman said:**
> If you've got the Nvidia drivers installed you should have an Nvidia settings tool in your System menu that can be used to detect and set up the TV.
I do not find the Nvidia settings tool. I have found the Nvidia driver in System, Where do I look now?

---

### Post by zipperback on 2009-09-19
If you don't see "Displays" when you click your system-> settings option, do you see the following?

```

System > Preferences > Screen Resolution

```

I guess it changed from 8.04 to 9.10 sorry about that.

I've attached a screenshot of the display panel that I have in 9.10 Karmic Koala which may you might be able to use for reference.

Try this...

connect the svideo to your tv set and set it to the appropriate channel for svideo input, then connect the svideo cable to the svideo connection to your computer, then turn on your computer, it should automatically recognize an additional available video display available.

If it still does not, then perhaps you will need to install a different video driver for your video card.

let me know please if this helps you. Thank you.


- zipperback

---

### Post by ded3d44 on 2009-09-19
Could you post the output of the xrandr command ? This can be done by opening a terminal and typing:
```
xrandr
```

---

### Post by Antedeluvian on 2009-11-01
I have been away from the challenge for  a month and a half for various reasons but have just started again to try to solve this challenge here in Vancouver. 

System > Preferences > Screen Resolution leads me to clone the the screens. When I apply this nothing happens.
If if restart the computer, then I get the Ubuntu Logo on the TV. Encouraging, a connection has been made, until the the Ubuntu screen asks for the user name. Then the TV looses the connection because I no longer have a clone setting. 

So I think there is some process with NVidia that I am missing which causes it to recognize that I  have connected  to a TV and locks in the connection. I don't know how to formulate the next question other than where should I be looking next?

 
> **zipperback said:**
> If you don't see "Displays" when you click your system-> settings option, do you see the following?

```

System > Preferences > Screen Resolution

```I guess it changed from 8.04 to 9.10 sorry about that.

I've attached a screenshot of the display panel that I have in 9.10 Karmic Koala which may you might be able to use for reference.

Try this...

connect the svideo to your tv set and set it to the appropriate channel for svideo input, then connect the svideo cable to the svideo connection to your computer, then turn on your computer, it should automatically recognize an additional available video display available.

If it still does not, then perhaps you will need to install a different video driver for your video card.

let me know please if this helps you. Thank you.


- zipperback

---

