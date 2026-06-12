---
title: "Windows Programs on Ubuntu"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Weighty Ghost on 2011-05-08
Hey Everyone,

The actual migrating from Windows to Ubuntu couldn't have went any smoother and I couldn't be anymore impressed with the current version of Ubuntu.

After searching and lurking the Wine threads, it looks like all of the programs I was wondering if would work on Linux can, w/ a tweak here and there as soon as I have time to invest a couple of late nights.

Problem is I have one specific program I absolutely can't live without and its an obscure one I can't get running (I think because it requires Microsoft .Net 2.0 Runtime). 
Namely, [SliQ]("http://www.sliqtools.co.uk/download-invoice-trial.aspx")

Anyway. just wanted to put together a shortlist of my available options...,

1. Are there alternative options to running a Windows programs other than Wine?
2. Are there chargeable support solutions available to look into?

---

### Post by rosencrantz on 2011-05-08
You could try playonlinux, [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/), but I think it's wine based, so it might not offer any improvements.
Or run a virtual windows on VirtualBox.
If you've already spent time on wine, you probably found this:
[http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754)
So, don't you get the .Net runtime to work, or does SliQ just not work with it?

---

### Post by Evdalo on 2011-05-08
I don't know about [SliQ]("http://www.sliqtools.co.uk/download-invoice-trial.aspx")

There is OpenBravo ERP

Take a look [HERE]("http://www.openbravo.com") before installing.

For install it type these codes in terminal

```

sudo add-apt-repository "deb http://archive.canonical.com/ubuntu natty partner"
sudo add-apt-repository "deb-src http://archive.canonical.com/ubuntu natty partner"[FONT=Verdana]
sudo apt-get update
[/FONT]sudo apt-get install openbravo-erp
```

---

### Post by lmarmisa on 2011-05-08
Consider to use virtualization. I like VirtualBox:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Weighty Ghost on 2011-05-08
> **Evdalo said:**
> I don't know about [SliQ]("http://www.sliqtools.co.uk/download-invoice-trial.aspx")

There is OpenBravo ERP

Take a look [HERE]("http://www.openbravo.com") before installing.

For install it type these codes in terminal

```
sudo apt-get install openbravo-erp
```

Thanks, I'll check that out if I can't get a virtualization solution happening.

---

### Post by kaldor on 2011-05-08
Nobody mentioned Codeweavers?

And yeah, if you need it flawless, try installing Windows in a virtual machine. If you have at least 2 Ghz and 3 GB RAM, it'll fly.

---

### Post by Weighty Ghost on 2011-05-08
Thanks Guys,

Total newb and wasn't aware of the Virtualbox possibility.
I'm reading all of the tutorials and FAQ's as I type...

Bummer that I'll have to pay MS again to reinstall there POS OS. 
If I'm understanding things so far, for someone like me who doesn't have alot of time for tweaks or learning efficient command-line usage I should get this up and running anyway, in case I need it.
Only question is, can my Netbook handle the required specs (?) -will find out shortly...,

Thanks everyone!,

---

### Post by Weighty Ghost on 2011-05-08
> **rosencrantz said:**
> If you've already spent time on wine, you probably found this:
[http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754)
So, don't you get the .Net runtime to work, or does SliQ just not work with it?

Yup,

Thats as far as I got last night (That was the page I was reading when I passed out lol).
Still no luck, but not a complete loss yet.
Embarrassingly, I do not know what "on a clean wine prefix[FONT=Verdana]" means, so I have to start fresh using that page as my guide, then run in a terminal and post the output in the Wine forum if I still cant get it to run. 
Problem is finding the time to play with it. [/FONT]

---

### Post by rosencrantz on 2011-05-08
Well, I had to google it too ;-)
[http://wiki.jswindle.com/index.php/Wine_Prefixes](http://wiki.jswindle.com/index.php/Wine_Prefixes)
It just means you'll have more success with a fresh wine configuration. 
The most simple way to do this would be to delete/rename the .wine folder in your home directory and then install the runtime before doing anything else.
However, this will remove your whole wine system including every program you have already installed there, so don't do it if you'll lose something irrecoverably. You'll have to reinstall all other programs running on wine as well.
Buying Windows just to run an accounting app on VirtualBox sounds like a bad deal. Virtual systems tend to run really slow, mine almost capitulates before iTunes on Win7 (admittedly, both are rather resource-hogging), and my laptop isn't exactly a netbook. If you have to, try to get XP, but I'd look into native solutions first, you might have less trouble with them.

---

