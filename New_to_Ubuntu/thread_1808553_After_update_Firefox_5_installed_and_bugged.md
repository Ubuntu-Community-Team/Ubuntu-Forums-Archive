---
title: "After update Firefox 5 installed and bugged"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by zanzibarwinds on 2011-07-20
Hi

Today I logged into Ubuntu (11.04) and ran the Update Manager without issue.

Opened Firefox (Was Firefox 4 a few days ago but think it updated to 5 today or recently, been a couple days since I used Ubuntu) and found the following issues:

1) Browser URL bar does not update to current page. When I visit a page and click a link it goes to that page no problem but is still showing the previous URL.

2) The back and Forward buttons are permanetly disabled.

3) As per 2 above, the context right click menu for Back, Forward and Refresh are greyed out.

4) Hovering the mouse cursor over a web link does not show the usual hand icon but gives me either the arrow or the I bar icon.

I tried to see if this could be fixed by doing the following but none proved to fix the issue:

1) Started firefox in safe mode (firefox -safe-mode) and reset everything and restarted firefox. No change.
2) Open firefox in safe mode and surf web, no change.
3) Removed ALL extendsions and add ons, restarted firefox, no change.
4) Un installed firefox from within the Software Centre, rebooted PC and reinstalled firefox without add ons, no change.

Downloaded Chrome and this works fine but I need firefox back to how it was before it became a train smash as I am in the middle of a deadline at the moment, is there known to fix the above issues please?

Failing that is it possible for me to install the last stable release of Firefox 4 in any manner?

Thanks in advance.

John

---

### Post by _0R10N on 2011-07-20
Are you sure you're using the 5.0 version and not a previous one?

---

### Post by LowSky on 2011-07-20
have you tried deleting, the ~/.mozilla folder from your home folder?

---

### Post by _0R10N on 2011-07-20
You can check the current version of firefox installed by executing

```
firefox -version
```

If it tells you that 5.0 is the installed version then, if you're sure that 4.0 worked fine, download it from Firefox's site and install it. Otherwise, if your current version is 4.0, then you could try LowSky suggestions.

Regards!

---

### Post by lovinglinux on 2011-07-20
> **zanzibarwinds said:**
> Failing that is it possible for me to install the last stable release of Firefox 4 in any manner?

Not recommended and probably not necessary. Looks like you got a bookmark database corruption with the upgrade. See instructions below on how to fix the problem.

> **LowSky said:**
> have you tried deleting, the ~/.mozilla folder from your home folder?

Most likely there is no need to do such drastic measure. I would start by deleting the file *places.sqlite* from your profile (~/.mozilla/firefox/<profilename>/places.sqlite). But make a backup first, because it holds your bookmarks. You can export your bookmarks through the Bookmark Manager and then import after deleting the file. Make sure to close Firefox before doing such operations.

If that doesn't work, then deleting the entire profile (~/.mozilla/firefox/<profilename>/) will certainly fix your problem. Make a backup first, so you can retrieve passwords and other stuff.

---

### Post by zanzibarwinds on 2011-07-21
Hi all

Thanks for your replies.

Firstly yes it is Firefox 5. Command firefox -version produces: Mozilla Firefox 5.0

Secondly my home folder does not seem to contain a ~/.mozilla folder oddly. I even looked in the home folder while logged in a SUDO thinking that it was a folder hidden to non root users. But still no Mozzila folder

As no ~/.mozzila folder existed I did a search for the file "places.sqlite" and found one but its located in a folder called "/proc/2362/fd/139"

No idea on what this folder is (Am new to ubuntu) so have not deleted it just yet.

Is there a way to fix the fact that no ~/.mozzila folder exists and will that alleviate the Firefox issues?

Regards and thanks.
John

---

### Post by lovinglinux on 2011-07-21
> **zanzibarwinds said:**
> Hi all

Thanks for your replies.

Firstly yes it is Firefox 5. Command firefox -version produces: Mozilla Firefox 5.0

Secondly my home folder does not seem to contain a ~/.mozilla folder oddly. I even looked in the home folder while logged in a SUDO thinking that it was a folder hidden to non root users. But still no Mozzila folder

As no ~/.mozzila folder existed I did a search for the file "places.sqlite" and found one but its located in a folder called "/proc/2362/fd/139"

No idea on what this folder is (Am new to ubuntu) so have not deleted it just yet.

Is there a way to fix the fact that no ~/.mozzila folder exists and will that alleviate the Firefox issues?

Regards and thanks.
John

Please post the output of:

```
ls ~/.mozilla/firefox
```

---

### Post by zanzibarwinds on 2011-07-21
hi Loving


john@john-ubuntu:~$ ls ~/.mozilla/firefox
1xkwiez0.default  Crash Reports  profiles.ini

---

### Post by lovinglinux on 2011-07-21
> **zanzibarwinds said:**
> hi Loving


john@john-ubuntu:~$ ls ~/.mozilla/firefox
1xkwiez0.default  Crash Reports  profiles.ini

Close Firefox and try the following, without changing anything in the command:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Start Firefox and test it. If it works, then you don't need to delete anything.

If it doesn't work, then close Firefox and try this:

```
mv ~/.mozilla/firefox/1xkwiez0.default/places.sqlite ~/.mozilla/firefox/1xkwiez0.default/places.sqlite.bak
```

---

