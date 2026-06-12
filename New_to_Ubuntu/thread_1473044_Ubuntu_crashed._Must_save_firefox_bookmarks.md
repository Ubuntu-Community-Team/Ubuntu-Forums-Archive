---
title: "Ubuntu crashed. Must save firefox bookmarks"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by tonsil on 2010-05-04
I tried to uninstall Evolution, but I must have chosen something irrelevant in synaptic manager. I knew something went wrong when I couldn't find the menu to change my startup applications. When I restarted I was prompted to login, but when I do that the screen briefly slashes and the login screen re-appears.

All of this is not important, because I plan to install a fresh kubuntu 10.04 anyway, but I really need my firefox bookmarks. Any idea of how to salvage them would be most appreciated. Thank you.

---

### Post by tonsil on 2010-05-04
oops. I mean the screen briefly flashes. LOL.

---

### Post by dearingj on 2010-05-04
When you get to the login screen, can you get to a terminal by pressing control+alt+F1? If so, try logging in through that terminal and then running this:

```
sudo apt-get install ubuntu-desktop
```

I'm guessing you removed one of the packages that ubuntu-desktop depends on, and so caused ubuntu-desktop to also be removed.

---

### Post by searchfgold6789 on 2010-05-04
If that doesn't work and apt-get thinks ubuntu-desktop is still installed and therefore not installable, try ```
sudo apt-get remove ubuntu desktop
```Then maybe a restart will happen, and ubuntu will look like text. There will be a terminal-type thing though.
```
sudo apt-get install ubuntu-desktop
```If that don't work:
Look online for the firefox directory in ubuntu. Boot from a live cd, Make another partition on your hard disk (system > administration) and make sure it is to the right of your existing ones and copy your existing firefox directory _on your hard disk not the cd_ to there. Then, if the directory is still the same in 10.04, you can paste it back after your fresh install and it may save all your bookmarks and even your passwords and stuff. But before you do any of this wait for someone to reply and tell you that I'm not crazy.
):P
 - search

---

### Post by emoguitarist06 on 2010-05-04
> **tonsil said:**
> I tried to uninstall Evolution, but I must have chosen something irrelevant in synaptic manager. I knew something went wrong when I couldn't find the menu to change my startup applications. When I restarted I was prompted to login, but when I do that the screen briefly slashes and the login screen re-appears.

All of this is not important, because I plan to install a fresh kubuntu 10.04 anyway, but I really need my firefox bookmarks. Any idea of how to salvage them would be most appreciated. Thank you.

If you can still start up firefox
Go to
Bookmarks>Organize Bookmarks>Import and Backup>Backup
and save the .json file to a flash or something of that nature.

---

### Post by techunit on 2010-05-04
Get the weave add-on for Firefox and it will back-up your bookmarks and sync them to any firefox with the add-on and your credentials.

---

### Post by tonsil on 2010-05-04
installing ubuntu-desktop worked like a charm! THANK YOU!! :)

---

### Post by lovinglinux on 2010-05-05
> **tonsil said:**
> installing ubuntu-desktop worked like a charm! THANK YOU!! :)

Now make sure you backup your Firefox profile regularly. You know, **** happens...See the Backup section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by lidex on 2010-05-05
I would highly recommend the xmarks extension:
[http://download.xmarks.com/download]("http://download.xmarks.com/download")
I have four separate installs of firefox all using the same synchronized bookmarks. FEBE is a good one also:
[https://addons.mozilla.org/en-US/firefox/addon/2109]("https://addons.mozilla.org/en-US/firefox/addon/2109")

---

### Post by xumuk37 on 2010-05-05
or use chrome... it does it automaticly when you check syncronization box...

---

### Post by lovinglinux on 2010-05-05
> **xumuk37 said:**
> or use chrome... it does it automaticly when you check syncronization box...

But it doesn't do a lot of things Firefox does and changing browsers is not what the OP wants.

---

