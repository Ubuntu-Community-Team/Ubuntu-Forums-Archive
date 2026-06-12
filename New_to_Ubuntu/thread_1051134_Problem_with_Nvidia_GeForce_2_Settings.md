---
title: "Problem with Nvidia GeForce 2 Settings"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by GSI on 2009-01-26
Here is the problem : When I open Nvidia X server Config and press save to X Server it says: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by Tomatz on 2009-01-26
> **GSI said:**
> Here is the problem : When I open Nvidia X server Config and press save to X Server it says: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

You need to run nvidia settings as root.

Open a terminal and:

```
gksu nvidia-settings
```


;)

---

### Post by GSI on 2009-01-26
That worked but now the top bar with the name and the close minimize and maximize options is gone! i really need it back

---

### Post by Tomatz on 2009-01-26
> **GSI said:**
> That worked but now the top bar with the name and the close minimize and maximize options is gone! i really need it back

That is probably because you misconfigured the xserver using nivdia settings.

Luckly nvidia settings creates a backup. Do this in a terminal to restore the backup:

```
cd /etc/X11
```

```
sudo cp xorg.conf.backup xorg.conf
```

**Now reboot**

;)

---

### Post by GSI on 2009-01-26
Not working :( :(

---

### Post by Tomatz on 2009-01-26
Do the commands again (i have edited the post above^), there was an error in my code :(

sorry.

---

### Post by GSI on 2009-01-27
It seems to be from the effects i turned them off now and everything is fine :)

---

### Post by Tomatz on 2009-01-27
> **GSI said:**
> It seems to be from the effects i turned them off now and everything is fine :)

You need to set compiz to either use metacity or emerald (window decoration). If you want to use compiz i can tell you how to do this?

---

### Post by GSI on 2009-01-27
> **Tomatz said:**
> You need to set compiz to either use metacity or emerald (window decoration). If you want to use compiz i can tell you how to do this?

It will be great.But do you have MSN or Skype?

---

### Post by Tomatz on 2009-01-27
> **GSI said:**
> It will be great.But do you have MSN or Skype?

Its better to do it on the forums, then others will be able to resolve a similar problem ;)

I'll be back in about an hour.

---

### Post by GSI on 2009-01-27
Oki tell me how :)

---

### Post by Tomatz on 2009-01-27
> **GSI said:**
> Oki tell me how :)

Do this:

[EDIT] **First, enable desktop effects.**

Then

```
sudo apt-get install emerald compizconfig-settings-manager
```

Then go to ***system, preferences, compizconfig settings manager*** (might be called ***advanced desktop effects settings***).

Now in the compiz settings manager find the ***"window decoration"*** plugin. Now **enable it by checking the checkbox** next to it.

Now it **_may_** be set up to use metacity by default so your window decorations **_may_** appear **_but_** we want nice shiny emerald window decorations so...

Enter the ***"window decoration"*** plugin by clicking on its icon.

Now there will be a box with ***"command"*** next to it. Put the following command into the box:

```
emerald --replace
```

Now you may need to **_logout_** to see changes. If not go to ***system, preferences, emerald theme manager***.

Now its all straight forward. There is a link below to a site with emerald themes:

[http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=cdb367b43b28fb305d00de3c196f0bff](http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=cdb367b43b28fb305d00de3c196f0bff) 

Enjoy

---

### Post by GSI on 2009-01-28
I cant it dosent works :@ 

Is there any way to remove compiz or reset to default settings?

---

### Post by Tomatz on 2009-01-28
Open a terminal and type:

```
emerald --replace
```

Then post the output.

Make sure compiz is running first though ;)

---

### Post by GSI on 2009-01-28
Dosent work...Cmon tell me how to remove the stupid compiz

I dont want to install ubuntu again..

---

### Post by Tomatz on 2009-01-28
> **GSI said:**
> Dosent work...Cmon tell me how to remove the stupid compiz

I dont want to install ubuntu again..

Remove it yourself. You have google you know...

Try talking a bit more respectfully.

---

### Post by GSI on 2009-01-28
I'm sorry.I will go wthout effects "_

---

### Post by Tomatz on 2009-01-28
> **GSI said:**
> I'm sorry.I will go wthout effects "_

Its ok ;)

I was in a crap, should have left it.

Do you still want to turn off compiz? If so go to ***System, Preferences, Apperance, Visual effects***.

---

### Post by GSI on 2009-01-29
Yes im like that now without effects they are turned off :)

---

### Post by Tomatz on 2009-01-29
> **GSI said:**
> Yes im like that now without effects they are turned off :)

Type the following into a terminal and post the output (text from terminal) here:

```
metacity --replace
```

---

