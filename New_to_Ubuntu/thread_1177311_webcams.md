---
title: "webcams"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Loon4000 on 2009-06-03
Hi,

I am new to ubuntu and have just installed the latest 9.04 version.

So far i have not had much trouble setting up my laptop to do what i want it to do.

The one problem i am getting however is trying to get my logitech E2500 quickcam to work on aMSN.

I have seen a few fixes about for this problem but as far none have worked.

Has anyone else had this same problem if so did you fix it and how as i am starting to get frustrated.

Does anyone have any step by step instructions that even this novice can follow.

Any help would be greatfully appreciated.

---

### Post by Sef on 2009-06-03
Moved to Absolute Beginners.

---

### Post by keplerspeed on 2009-06-03
Ok first thing plug in the webcam and enter this code into the terminal to see what its doing:
```

ls /dev/video*

```

Hopefully the output in the terminal will be similar to /dev/video0

If so, install 'camorama' via synaptic. Open the camorama app (in applications menu somewhere) and webcam should be working. Then we can get onto configuring aMSN...

HOWEVER, if the output from ls /dev/video* is nothing, then the driver is not present. In this case, we can use the gspca driver. I can help with this is required. See how the above goes first.

As a start, this is how I set up my logitech webcam back a year ago [http://ubuntuforums.org/showthread.php?t=651375](http://ubuntuforums.org/showthread.php?t=651375)

---

### Post by Loon4000 on 2009-06-04
Cheers i will give this a go and let you know how i go on.


DESIGNED FOR WINDOWS XP BUT RUNNING UBUNTU

---

### Post by Loon4000 on 2009-06-06
Ok tried ls/dev/video and it just states that the directory does not exist.

What do i do next?

---

### Post by jrox717 on 2009-06-06
the code should be 

```
 ls /dev/video* 
```

---

### Post by Loon4000 on 2009-06-08
Hi,

All of a sudden my old webcam has started working i carn't explain it it just happened :p

Thanks for your help guys.

---

### Post by Loon4000 on 2009-06-17
Ok I spoke to soon.

aMSN recognises my cam but will not stream the video to anyone on my contact list.

Any ideas on how to fix this?

---

