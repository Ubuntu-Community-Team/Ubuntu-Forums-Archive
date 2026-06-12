---
title: "So called Safe Mode in UBUNTU (graphics problem)"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by ifhamr on 2009-10-10
Hii im totally new to UBUNTU. At the moment i am using UBUNTU 9.04 on a HP DV4000 Laptop (Standard Configurations)

Everything seemed good till I installed was curious to try Advanced Desktop Effects and enabled all checks under Effects.

Now I see that ( No idea if my Graphic cards is supporting), everywhere i point my mouse the desktop turns black (forms a patch like thing), and no MENUS are accessible. 

I would be glad if someone can help me to restore the graphic effects back ( i.e like using safemode in WIN XP or Vista)

Thx

Ifham

---

### Post by aesis05401 on 2009-10-10
I don't have 9.04 handy, but people usually recommend trying the following first:
ctrl+alt+F2
login
metacity --replace
logout
ctrl+alt+F7


Does this help?

---

### Post by ConXtionS on 2009-10-10
How do you guys REMEMBER all this stuff?

---

### Post by ifhamr on 2009-10-10
Where should I type this?

Since no Menus are accessible.

awaiting ur suggestion.

---

### Post by aesis05401 on 2009-10-10
When you press ctrl+alt+F2 a terminal should open.  It does not?

---

### Post by aesis05401 on 2009-10-10
> **ConXtionS said:**
> How do you guys REMEMBER all this stuff?

The problem is not remembering.. it's remembering the right thing at the right time ;) 

I'm not sure this will solve the OP's problem, but running metacity --replace tells metacity (an alternate window manager)to attempt to replace the running WM so the menus can be accessed again.

---

### Post by ifhamr on 2009-10-10
it does..

am i just to type metacity replace??

---

### Post by aesis05401 on 2009-10-10
If you have logged in succesfully you must now type ```

metacity --replace

```

The dashes must be the same when you type it in.  After this type 'logout' then press ctrl+alt+F7 to go back to your normal desktop.  

Please tell us if your menus have returned or if you have any issue I did not describe.

Edit: That may require a 'sudo' before it, in which case you will need to enter your password again... Example: sudo metacity --replace

---

### Post by ifhamr on 2009-10-10
When types with sudo or without

IT says :

window manager error : unable to open  X display

---

### Post by aesis05401 on 2009-10-10
I see.  I just double checked the help.Ubuntu.com compiz page:[https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion").

It recommends the process we just attempted, so something has changed.  I will see what I can dig up and post back.

---

### Post by aesis05401 on 2009-10-10
Alright... I have an answer that works on my machine, but I am not running jaunty, and I had to test it by crashing my WM and then trying to restart from ctrl+alt+F2, and this worked:
```

metacity --display=:0.0 --replace &

```

The additional --display parameter tells X server we want to talk to the default graphical session.  The '&' is there so the command will complete properly.  Again, please post back and let us know if this works.  If it works I will go edit the wiki.

---

### Post by ifhamr on 2009-10-10
> **aesis05401 said:**
> Alright... I have an answer that works on my machine, but I am not running jaunty, and I had to test it by crashing my WM and then trying to restart from ctrl+alt+F2, and this worked:
```

metacity --display=:0.0 --replace &

```The additional --display parameter tells X server we want to talk to the default graphical session.  The '&' is there so the command will complete properly.  Again, please post back and let us know if this works.  If it works I will go edit the wiki.


WORKS Perfect...:KS

Thanks For all your help & effort buddy:P

---

### Post by aesis05401 on 2009-10-10
We helped everyone together :)  I will update the docs so others will know in the future.  Welcome.

---

### Post by quinnten83 on 2009-10-10
i think it's just alt+F2.
you get the run dialog and you can enter metacity --replace.
This will change the windowmanager from compiz to metacity. What you get is a complete environment but without compositing (i.e. destop effects).You should be able to access ccsm to change the effects back. after you're done, you can start the effects again, by pressing alt+F2 and entering the command to start compiz.
I think it's compiz-config --replace, but don't quote me on that...

---

### Post by MisterH on 2010-07-05
Hi guys, I'm not sure if I have a hardware problem or if something is going wrong following one of the updates. I have an old NVidia card and I manage to get Ubuntu 10.4 installed and the enhanced graphics enabled after loading the recommended Nvidia driver.
 
But after a while the graphics get corrupted - like there is a memory leak, things don't get drawn or they appear with pixels missing or stripey patterns that disappear when I roll-over. Sometimes window controls aren't drawn properly and the window can't be closed.
 
There was also a power cut last night and since then, my PC now won't display the GUI - I sometimes see the ubuntu splash screen, but then I get a green stripe about 25% from the left, I eventually hear the little drum, which means the logon screen has loaded, but the screen is black.
 
I can get the system into a console, if I press ctrl-shift & F1 before I hear the drum.
 
before I log-in to the console session, I see this error at the top of the screen;
 
```
 
 Error requesting Region 4300 .. 433F for SMB2
nforce2_smbus_0000:00:01.1: Error probing SMB2

```
(which may be a red herring)
 
and when I type the metacity commands I get 
 
```
Window manager error: unable to open X display
```
 
for the short version and
 
```
Window manager error: Unable to open X display :0.0
```
 
for the long version.
 
Last time this happened I ended up re-installing ubuntu from the CD but this time I have loaded quite a lot of stuff plus I have a hot girl on my desktop wallpaper :)
 
Is there a way to recover without rebuilding please?
 
Can I get more diagnostic info somehow?
 
Should I buy a new PC? This one is a bit old - 2 years or so, so I might be better off with a multi-core CPU and a newer graphics card... What is the minimum Nvidia chipset number I should get? (need to keep costs down)
 
Thanks for any help you can offer - it's a bit frustrating, but I want to learn how to fix it.

---

