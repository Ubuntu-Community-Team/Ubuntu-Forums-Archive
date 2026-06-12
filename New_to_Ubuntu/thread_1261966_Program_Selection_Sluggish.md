---
title: "Program Selection Sluggish"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by daniell59 on 2009-09-09
Ubuntu 9.04
Intel Dual Core
4 GIG Memory

Let me explain by example.
If I am in Firefox and I want to change to another open program such as Thunderbird mail, the change sometimes takes several seconds. It seems to get progressively worse from the time that I try to go back and forth.
Any insight will be helpful.

Thakns

---

### Post by NightwishFan on 2009-09-09
Are you running Compiz? If so try to disable it. Also open a terminal and post the top three process in the list, using the command:

```
top
```

---

### Post by daniell59 on 2009-09-09
> **NightwishFan said:**
> Are you running Compiz? If so try to disable it. Also open a terminal and post the top three process in the list, using the command:

```
top
```

Please excuse my ignorance, but what is Compiz?

---

### Post by daniell59 on 2009-09-09
> **daniell59 said:**
> Please excuse my ignorance, but what is Compiz?

Here is a screen shot. I don't know what this all means.

---

### Post by NightwishFan on 2009-09-09
My apologies. Desktop effects. Go to System -> Preferences -> Appearence. Then a window will open. The last tab is called visual effects, please set it to none and see if performance improves. If it is already at none, then move on to step 2.

Open Applications -> Accessories -> Terminal and a black window will open. Type this:
```
top
```
Then press enter. A bunch of information will appear. After a few seconds, press q. (as in Quit)

Copy and paste the information here.

---

### Post by daniell59 on 2009-09-09
> **NightwishFan said:**
> My apologies. Desktop effects. Go to System -> Preferences -> Appearence. Then a window will open. The last tab is called visual effects, please set it to none and see if performance improves. If it is already at none, then move on to step 2.

Open Applications -> Accessories -> Terminal and a black window will open. Type this:
```
top
```
Then press enter. A bunch of information will appear. After a few seconds, press q. (as in Quit)

Copy and paste the information here.

Thanks,
I just set it to none. So far, it seems to be now working perfectly. Please explain what I did.

Thanks again!

---

### Post by Perfect Storm on 2009-09-09
Compiz is a application that make your Video card to render the interface (3D). It seems that either you video card is either poor supported or there may be a driver you need to install to switch in on again.

Do you know which card you have? Or check System tab ---> Administration ---> Hardware Drivers to check if any drivers are available.

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> Compiz is a application that make your Video card to render the interface (3D). It seems that either you video card is either poor supported or there may be a driver you need to install to switch in on again.

Do you know which card you have? Or check System tab ---> Administration ---> Hardware Drivers to check if any drivers are available.

This is my video card.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121259](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121259)

---

### Post by Perfect Storm on 2009-09-09
Ah, ATI.

Try check if ATI restrictive driver is available through "Hardware Driver".

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> Ah, ATI.

Try check if ATI restrictive driver is available through "Hardware Driver".

Where do I go from here?

---

### Post by Perfect Storm on 2009-09-09
It seems it is installed. Did you also restart Ubuntu after that?

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> It seems it is installed. Did you also restart Ubuntu after that?

Yes

---

### Post by Perfect Storm on 2009-09-09
Lets try this (note, I'm a nvidia guy so I don't have any experience with ATI); Uninstall the driver, reboot and see if it picks up the Open Source driver. If it seems better you can use that instead - I'm not sure if you can enable compiz without it installing the restrictive drivers.

---

### Post by daniell59 on 2009-09-09
> **daniell59 said:**
> Yes

How do I get it to pick up the open source driver?

---

### Post by Perfect Storm on 2009-09-09
> **daniell59 said:**
> How do I get it to pick up the open source driver?

Ubuntu should come with it by default, but you might want to ask one of our ATI guys on the forum if it's correct, as I'm only to Nvidia.

---

### Post by daniell59 on 2009-09-09
> **daniell59 said:**
> How do I get it to pick up the open source driver?

Also, should I change anything in visual effects?

---

### Post by Perfect Storm on 2009-09-09
> **daniell59 said:**
> Also, should I change anything in visual effects?

If it picks up the Open Source driver? Give it a try, it may say it want to install the restrict driver.

---

### Post by daniell59 on 2009-09-09
uninstalled then installed video driver. Things are worse. I don't know how to fix my desktop. Cannot see the panels anymore when I use firefox.

---

### Post by Perfect Storm on 2009-09-09
<alt>+<F2>

type;
```
jockey-gtk
```
To get the app that install the driver.

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> <alt>+<F2>

type;
```
jockey-gtk
```
To get the app that install the driver.

Somehow I no longer have the little square box, maximize, minimize on the right side of any program. How do I get it back?

Thanks

---

### Post by Perfect Storm on 2009-09-09
Is compiz on or off?

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> Is compiz on or off?

Please explain what compiz.

---

### Post by Perfect Storm on 2009-09-09
Compiz is the 3D effect we talk about earlier.


Nevertheless, try this and see if it helps;
<alt>+<F2>
```
metacity --replace
```

---

### Post by daniell59 on 2009-09-09
Since I do not know what is going on, I took a digital image of the screen. I hope someone can get me past this problem.

Thanks

---

### Post by Perfect Storm on 2009-09-09
Okay, is it only firefox that is missing the "Window frame" or is all the apps?

If it's all; Did you tried the **metacity --replace** command?

---

### Post by daniell59 on 2009-09-09
> **artificial intelligence said:**
> okay, is it only firefox that is missing the "window frame" or is all the apps?

If it's all; did you tried the **metacity --replace** command?

all

---

### Post by Perfect Storm on 2009-09-09
Okay, lets try a different angle.

I assume you can see the upper panel if you minimize firefox?
Open the terminal (Applications ---> Accessories ---> terminal)

```
sudo apt-get install fusion-icon
fusion-icon
```

An Notify icon appears (in upper right panel), right click on it.

Under "Select Windows Manager" choose Metacity

and

Under "Select Window Decoration" select GTK Window Decorator

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> Okay, lets try a different angle.

I assume you can see the upper panel if you minimize firefox?
Open the terminal (Applications ---> Accessories ---> terminal)

```
sudo apt-get install fusion-icon
fusion-icon
```

An Notify icon appears (in upper right panel), right click on it.

Under "Select Windows Manager" choose Metacity

and

Under "Select Window Decoration" select GTK Window Decorator

The problem is that I cannot minimize firefox.

---

### Post by Perfect Storm on 2009-09-09
You can see the lower panel, right?

Right click on the firefox in the lower panel and choose "minimize" or "move".

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> You can see the lower panel, right?

Right click on the firefox in the lower panel and choose "minimize" or "move".

I did what you instructed and I do not get minimize or move

---

### Post by Perfect Storm on 2009-09-09
Okay, strange...


Copy this to a text file;
> Okay, lets try a different angle.

I assume you can see the upper panel if you minimize firefox?
Open the terminal (Applications ---> Accessories ---> terminal)

Code:
sudo apt-get install fusion-icon
fusion-icon
An Notify icon appears (in upper right panel), right click on it.

Under "Select Windows Manager" choose Metacity

and

Under "Select Window Decoration" select GTK Window Decorator
Then;
<alt>+<F2>
```
killall firefox
```

Now follow the guide I quoted.

---

### Post by daniell59 on 2009-09-09
> **Artificial Intelligence said:**
> Okay, strange...


Copy this to a text file;

Then;
<alt>+<F2>
```
killall firefox
```

Now follow the guide I quoted.

For some reason, I cannot type in terminal. The keyboard does not generate letters. I am out of ideas.

---

### Post by daniell59 on 2009-09-09
> **daniell59 said:**
> For some reason, I cannot type in terminal. The keyboard does not generate letters. I am out of ideas.

I really hope that I do not have to reinstall Ubuntu. I am at loss where to go from here. I cannot minimize either firefox or thunderbird. There is probably and easy fix. I just do not know what it is.

---

### Post by Perfect Storm on 2009-09-10
Do a reboot, to get them closed then.


<alt>+<ctrl>+<F1>
username
password (you can't see it when typing)
sudo reboot

---

### Post by daniell59 on 2009-09-10
Thanks, I am not at that computer now, I will try it later.
I really do not understand what is going on. The trouble started when I uninstalled the video driver. I reinstalled it however. Everything looks a little funny, even the desk top. I do not know how to desribe it. It looks like the desktop is too high up.
Thanks again for your kind assistance in this matter.

---

### Post by daniell59 on 2009-09-10
I did as you suggested. No change. I still cannot minimize my programs. I am open to other suggestions.

---

### Post by Perfect Storm on 2009-09-10
You can do simple in firefox (and I guess thunderbird too);

In the **file** tab ---> **quit**

---

### Post by daniell59 on 2009-09-10
The programs block my top panel.

---

### Post by Perfect Storm on 2009-09-10
If it does you can get to the applications tab ---> accessories ---> terminal and what I instructed earlier.

---

### Post by ugm6hr on 2009-09-10
> **daniell59 said:**
> For some reason, I cannot type in terminal. The keyboard does not generate letters. I am out of ideas.

Does it generate letters in any other application?  

The possibilities are:
Your keyboard is not working / not plugged in.
You have a problem with the prompt in Terminal.

This is unrelated to the original problem of having no border to the Firefox windos.

In summary (for you and others who may be trying to help):
You use the "Gnome" (default for Ubuntu) desktop environment.
You have an ATI graphics card.
You currently have "No visual effects"
You have lost your window manager (which creates the frames around all your applications)
You can no longer type anything (unclear why)

---

### Post by daniell59 on 2009-09-30
By typing sudo apt-get install fusion-icon in the terminal I was able to get the top panel back, but when I launch any application it covers it up and I cannot minimize it.

Thanks

---

