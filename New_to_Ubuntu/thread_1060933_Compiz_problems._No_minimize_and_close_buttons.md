---
title: "Compiz problems. No minimize and close buttons"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Jynxx on 2009-02-05
Good Morning All,

Yesterday I installed a new theme which has caused me some problems with what I assume to be compiz. Now when I open firefox, I don't have the top border with the minimize and close buttons. I uninstalled the theme but am still having the same problem. Any way that I can fix this without having to completely removing ubuntu and reinstalling it?

Thanks!

---

### Post by gettinoriginal on 2009-02-05
Hit F11 twice, then manually minimize your page, then close firefox, reopen, and maximize normally.  :p

---

### Post by Jynxx on 2009-02-05
crud, that didn't work

---

### Post by leonardo_neo on 2009-02-05
> **Jynxx said:**
> crud, that didn't work

What theme did you install? Was it GTK +2, or Firefox theme, or something tweaking you did in compiz?

Anyway, I am not sure what exactly is causing the problem, if it is theme related to GTK, then you can try

System-->Preference-->Appearance--->Theme--->Customize--->Window border--->and then try changing it to some other theme say 'Human'.

---

### Post by bumanie on 2009-02-05
What type and model of graphics card are you running?

---

### Post by Tews on 2009-02-05
Open a terminal window and type .... MetaCity ==replace

That should do the trick ..;)

---

### Post by drs305 on 2009-02-05
You mentioned firefox. If it's more universal, opening the Compiz Configuration Settings Manager, Effects and enable "Window Decoration" will restore the borders. 

If you don't have the settings manager installed:
```

sudo apt-get install compizconfig-settings-manager

```

To Run: "ccsm" or System, Preferences, CompizConfig Settings Manager.

---

### Post by binbash on 2009-02-05
> **Tews said:**
> Open a terminal window and type .... MetaCity ==replace

That should do the trick ..;)

It is metacity --replace ;)

---

### Post by Therion on 2009-02-05
Another possible solution:

Open CCSM (Compiz Config Settings Manager).
Scroll down to the **Utilities** section and open the **Workarounds** plugin.
*UN*-check the option for "Legacy Fullscreen Support".
You may need to log out and log back in to make the fix "stick".

---

