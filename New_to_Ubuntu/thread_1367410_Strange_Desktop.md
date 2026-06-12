---
title: "Strange Desktop"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by ksrijith on 2009-12-29
Hi,
I've just installed Ubuntu 9.10. This is the first time i'm using Ubuntu and the desktop that came default seems a bit strange I would instead like to use a default GNOME desktop. 

The attached screenshot shows the desktop with all these links. Actually its exactly like the main menu. Now is there some way to remove this and get back a simple plain desktop?
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]
Thanks

---

### Post by Cheesemill on 2009-12-29
What you've done is installed UNR (Ubuntu Netbook Remix) instead of standard Ubuntu.

---

### Post by junapp on 2009-12-29
not sure exactly how to get a gnome desktop back, but I suspect  installing 'gnome' or 'ubuntu-desktop' *might* do it - wait for a response from someone more sure.

What you are seeing is the Ubuntu Netbook remix
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)
[https://answers.edge.launchpad.net/netbook-remix](https://answers.edge.launchpad.net/netbook-remix)

This link may assist:
[https://answers.edge.launchpad.net/netbook-remix/+question/90183](https://answers.edge.launchpad.net/netbook-remix/+question/90183)
> 
[Andrew]("https://edge.launchpad.net/%7Ewilliam-andrew-lane") said     on 2009-12-03:       You do not have to install the full version of 9.10 to switch to the regular desktop. All you need to do is right click the ubuntu logo on the left of the panel at the top of the screen - and click "Remove from Panel." Then right-click again in the same spot and click "Add to Panel" and select "Main Menu" or "Menu Bar" depending on which one you like better (I went with the normal Main Menu). If the top panel "auto-hides" right-click it once again and select "Properties" and de-select "Auto-Hide." Last but no least go into the Menu -> System -> Startup Applications and de-select "Netbook Launcher" (this will get rid of the Clutter interface that shows all your icons on the desktop.
 There you have it - the way Ubuntu looks normally while keeping the drivers and kernel specific to netbooks.
 Andrew




---

### Post by HappyFeet on 2009-12-29
Here is regular ubuntu. [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by tom.swartz07 on 2009-12-29
> **HappyFeet said:**
> Here is regular ubuntu. [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

WAIT!

You dont have to re-install.

Just open synaptic package manager and search for 'ubuntu-netbook'
there should be a package that is marked with netbook desktop manager or something similar. Uninstall that and search for 'ubuntu-desktop' and install that.

this will remove the old manager that you dont like, and install the desktop that you want.

DO NOT DO ONE WITHOUT THE OTHER, as it will leave you without a desktop environment, and make things slightly more difficult to manage.

Be aware that the download is going to be around 400 megabytes, but its a ton easier than completely re-installing your system

---

### Post by audiomick on 2009-12-29
> **tom.swartz07 said:**
> WAIT!

DO NOT DO ONE WITHOUT THE OTHER, as it will leave you without a desktop environment, and make things slightly more difficult to manage.



This would mean, to be on the safe side, install ubuntu-desktop first, then un-install ubuntu-netbook.

Having said that, as long as you don't log out in the middle of things, I don't think you will have a problem.

---

### Post by LowSky on 2009-12-29
open up terminal and use this command

```
sudo apt-get remove window-picker-applet maximus go-home-applet human-netbook-theme ume-launcher
```

There's an even simpler solution, if you don't mind leaving the software modules for the netbook interface in place, just not active. Go to System->Preferences->Switch Desktop Mode

---

### Post by LowSky on 2009-12-29
> **audiomick said:**
> This would mean, to be on the safe side, install ubuntu-desktop first, then un-install ubuntu-netbook.

Having said that, as long as you don't log out in the middle of things, I don't think you will have a problem.

UNR is Ubuntu with extra packages for netbook use... do you people even study what the software your using does? Too many people responded with "install regular Ubuntu". Please know what you telling someone to do is actually beneficial before posting such nonsense

---

### Post by audiomick on 2009-12-29
> **LowSky said:**
> UNR is Ubuntu with extra packages for netbook use... do you people even study what the software your using does? Too many people responded with "install regular Ubuntu". Please know what you telling someone to do is actually beneficial before posting such nonsense

So does that mean that UNR has a different desktop as well as the standard desktop, or just different tool bars or whatever to make the layout more useful? Not having used it, I don't know.

My post was actually intended to avoid leaving the op without a GUI, which is what the previous advice sounded like it would leave him open to.

---

### Post by HappyFeet on 2009-12-29
> **LowSky said:**
> UNR is Ubuntu with extra packages for netbook use... do you people even study what the software your using does? Too many people responded with "install regular Ubuntu". Please know what you telling someone to do is actually beneficial before posting such nonsense

No need for the attitude. Save that for the community cafe. Flying off the handle helps no one.

Plus, it may be beneficial for the OP to actually have a regular ubuntu disk on hand for future use. Ever think of *that*?

---

