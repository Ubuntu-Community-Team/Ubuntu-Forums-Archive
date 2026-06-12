---
title: "Security:- Firestarter freezes on shut down"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by brian mellett on 2009-02-03
Firestarter freezes at shut down or hibernate. Firestarter and the pc can only be shut down forcefully(switch off). If left on the screen eventually blanks except for a small flashing cursor in top left corner. On start up ubuntu8-10 loads normally but stalls for a period at the screen display of "video mode not supported".Even though installed it shows it is switched off but connected through "etho 0 device. I am offerred some configeration choices but apart from ticking "etho 0" do not understand choices. I have another pc connected wirelessly running XP and a printer. Is this caused by my second pc. What do the configuration choices mean and what should they be set to?. As a beginner simple explanations and stating the mere basics if possible would be appreciated. I love this linux when working! Regards from Brian who's still smiling.

---

### Post by brian_p on 2009-02-03
> **brian mellett said:**
> 

As a beginner simple explanations and stating the mere basics if possible would be appreciated.

Remove firestarter using your package manager or, in a terminal, do

```
apt-get remove --purge firestarter
```

Now observe and report the behaviour of your machine.

---

### Post by billgoldberg on 2009-02-03
> **brian mellett said:**
> Firestarter freezes at shut down or hibernate. Firestarter and the pc can only be shut down forcefully(switch off). If left on the screen eventually blanks except for a small flashing cursor in top left corner. On start up ubuntu8-10 loads normally but stalls for a period at the screen display of "video mode not supported".Even though installed it shows it is switched off but connected through "etho 0 device. I am offerred some configeration choices but apart from ticking "etho 0" do not understand choices. I have another pc connected wirelessly running XP and a printer. Is this caused by my second pc. What do the configuration choices mean and what should they be set to?. As a beginner simple explanations and stating the mere basics if possible would be appreciated. I love this linux when working! Regards from Brian who's still smiling.

It must be noted that firestart does more harm than good for beginners.

It's not needed.

If you, for some reason, need to change something, use "ufw".

---

### Post by handydan918 on 2009-02-03
I don't think there is anything wrong with firestarter, contrary to most of the opinions here.
However, it should be noted that firestarter does NOT need to be running. It is only a configuration tool for iptables, and should be closed after configuration is done. 
That being said, if you have used firestarter to do things you aren't sure of, you can do a lot of mischief to any linux system by fiddling with iptables. The whole system is based on a client-server model (yes, even inside the box) and borking the packet handling can have really adverse effects.

---

### Post by brian mellett on 2009-02-03
Thanks everybody .Typing apt-get etc gives "13 permission refused etc." so will take the advice of the rest of you and remove the prog. Perhaps Linux isn't for me? Thanks again Brian

---

### Post by brian_p on 2009-02-03
> **brian mellett said:**
> Thanks everybody .Typing apt-get etc gives "13 permission refused etc." so will take the advice of the rest of you and remove the prog. Perhaps Linux isn't for me? Thanks again Brian

I forgot 'sudo'.

```
sudo apt-get remove --purge firestarter
```

The purpose of removing it is to eliminate it as source of any problem you think you have. The message about video mode: do you still get that?

---

### Post by brian mellett on 2009-02-03
file:///home/brian/sudo%20apt-%20firestarter

Thanks brianp I try not to give up. Have come unstuck with"sudo" addition to command. I have got to sort somthing out as having removed  "Firestarter I still cannot close down with out switching off power. Waiting hopefully for a reply. Brian mellett.

---

### Post by brian mellett on 2009-02-03
Brianp, forgot to say Yes to video message still on screen, but has been there long before this problem. brian mellett

---

### Post by brian mellett on 2009-02-08
Still stuck with shut-down freezing if "hibernating, ok on "shut down. Unable to get passed "Permission 13 denied" message. I have removed Firestarter. As I like to "hibernate" can anybody take me forward to complete the excercise? Thankyou.

---

### Post by brian_p on 2009-02-08
> **brian mellett said:**
> Still stuck with shut-down freezing if "hibernating, ok on "shut down. Unable to get passed "Permission 13 denied" message. I have removed Firestarter. As I like to "hibernate" can anybody take me forward to complete the excercise? Thankyou.

Forget about firestarter, it's not the problem.

What the problem is I do not have a clear idea about but it could be hardware related I suppose. I have only recently begun to use hibernate but from the command line:

```
sudo pm-suspend

```

The pm-utils package needs to be on the system. Try it.

---

### Post by ptn107 on 2009-02-08
Just use the built in 'ufw'.  It's as easy as running this one command and forgetting about it.  As long as your not running server daemons on your machine your golden.

```
sudo ufw enable && sudo ufw default deny
```

---

### Post by brian mellett on 2009-02-09
> Thanks for coming back Brianp. "sudo pm-suspend " caused pc to freeze so I forced a shut down. On restart additional writing appeared on start up,and on next "hibernation" success.But on next start up pc froze with "video mode not supported. A further forced shut down was necessary but pc now performs ok. I,ll let you know later if further problems experienced. Any ideas on "video mode " message? Thanks for your expertise. B;)rian

---

### Post by brian_p on 2009-02-10
> **brian mellett said:**
> 

Any ideas on "video mode " message?

If you are getting the message while X is loading it possibly means you have a video mode in its configuration file which your video adaptor does not support. Try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by brian mellett on 2009-02-17
I have tried all the codes suggested and can only close down by "shut down"."Vidio mode...."still displays on start up. Unfortuneately I do not  understand fully the language used in the instructions. Problem not solved.

---

