---
title: "Help! Intel Corporation 82945G/GZ Integrated Graphics Controller"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-03-05
Does anyone know how to install drivers for 

Intel Corporation 82945G/GZ Integrated Graphics Controller?

---

### Post by oldos2er on 2009-03-05
```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

```

---

### Post by ivanvajar on 2009-03-05
Thanks! Everything seems OK, but I'm still unable to make Compiz do it's work. Any idea?

---

### Post by avtolle on 2009-03-05
I don't know if this applies to your situation, as I neither have an Intel graphics chip, nor do I use (or want to use) compiz, but IIRC, there is a problem with certain intel drivers for Ubuntu and enabling desktop effects; in other words, the driver won't handle it. When you go to System>Preferences>Appearance and click on the effects tab, are you able to enable these (compiz) or do you get an error message to the effect that this is not available to you?

---

### Post by ivanvajar on 2009-03-05
I get the message that effects can't be enabled.

---

### Post by Therion on 2009-03-05
I have heard that using Synaptic Package Manager to remove all the installed packages containing "fglrx" gets Compiz working on your particular chipset.

*Unconfirmed.  **Use at your own risk.***

---

### Post by ivanvajar on 2009-03-05
It's all disabled, but Compiz doesn't work. Any idea?

---

### Post by avtolle on 2009-03-05
I think that you may be out of luck with getting compiz to work with your chipset.

---

### Post by ivanvajar on 2009-03-05
I know that there are other desktop managers. Do you know about any?

---

### Post by avtolle on 2009-03-05
Other desktop managers won't help you get compiz working if the driver for your chip doesn't support it in Ubuntu (or its derivatives), if this is what you are asking. There may be other distros where compiz works with your chip due to using a different driver; I don't know which one(s) might do that for you.

---

### Post by ivanvajar on 2009-03-05
Thank you all, folks.

---

### Post by pragaad on 2009-04-23
help please.
same graphics card. cant enable desktop effects. can i use animation softwae without any problem. i also have intrepid ibex. i posted a thread about my whole problem help me.

---

### Post by dhane1000 on 2009-04-25
I also have the same built in graphics card which is in GX520 , i have no problem with it. compiz works like a charm., :P

---

### Post by ivanvajar on 2009-04-25
As I posted on another threat, I solved this problem by installing SuperUbuntu. Check it out.

---

### Post by frank_claessen on 2009-07-28
> **ivanvajar said:**
> I know that there are other desktop managers. Do you know about any?

Hi all,

I have the exact same chipset and compiz just works fine. However, I am using Kubuntu Jaunty and I can activate the effects and it works just fine. Although I have to admit that I seldom use these effects. It's fun but not very effective imho.

Cheers Frank

---

