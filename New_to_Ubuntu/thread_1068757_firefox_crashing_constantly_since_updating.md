---
title: "firefox crashing constantly since updating"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-02-13
the other day 3.0.6 got added to the repositories for updating and since then firefox has been crashing 2 or 3 times a day when before it almost never happened.  has this been happening to anyone else?

---

### Post by -jay- on 2009-02-13
same here its crashing on several sites for me

---

### Post by HavocXphere on 2009-02-13
Flakey here too. Started before I had even restarted FF after the upgrade.

It doesn't crash, but it keeps opening a small 1cmx1cm window in the middle of the screen. Sometimes there is something in it when I maximize it, sometimes not.:confused:

---

### Post by jou770d on 2009-02-13
Weird, the only problem it's doing here is offering to save .php files instead of showing them.
But that started even before the update.

---

### Post by sydbat on 2009-02-13
> **Amarus said:**
> Weird, the only problem it's doing here is offering to save .php files instead of showing them.
But that started even before the update.This is due to some problem with the server/DB of the pages you visit. I have been getting this for years, in both Windows (IE and FF) and Ubuntu. I use it to troubleshoot the forum/website I run.

To the OP ( and the others expressing concerns) - what sites crash? Are they graphics intensive? Do they use Java or Flash?

---

### Post by jou770d on 2009-02-13
> **sydbat said:**
> This is due to some problem with the server/DB of the pages you visit. I have been getting this for years, in both Windows (IE and FF) and Ubuntu. I use it to troubleshoot the forum/website I run.
Actually I'm dual-booting Vista with Ubuntu and this isn't happening there (latest fox running on both). Plus it's not one or two sites, it's pretty much every forum I go to (this one included) and some other websites.

---

### Post by sydbat on 2009-02-13
> **Amarus said:**
> Actually I'm dual-booting Vista with Ubuntu and this isn't happening there (latest fox running on both). Plus it's not one or two sites, it's pretty much every forum I go to (this one included) and some other websites.OK...that is weird. Have you gone to the FF site and [looked at the release notes]("http://www.mozilla.com/en-US/firefox/3.0.6/releasenotes/") to see if your issue is known?

If it is not in the release notes, you can [find/file a bug]("https://bugzilla.mozilla.org/").

EDIT - There are [a few bug reports]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=save+php") about this. The answers are basically what I mentioned in my previous post.

Also, what extensions do you have? One of them could be conflicting, causing FF to crash.

---

### Post by jou770d on 2009-02-13
> **sydbat said:**
> OK...that is weird. Have you gone to the FF site and [looked at the release notes]("http://www.mozilla.com/en-US/firefox/3.0.6/releasenotes/") to see if your issue is known?

If it is not in the release notes, you can [find/file a bug]("https://bugzilla.mozilla.org/").

EDIT - There are [a few bug reports]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=save+php") about this. The answers are basically what I mentioned in my previous post.

Also, what extensions do you have? One of them could be conflicting, causing FF to crash.

Yeah I checked those bugs but it doesn't seem like the same problem. Same extensions are running on Vista with no problems but I'm gonna try using safemode to see if that helps. Maybe one of them isn't that *nix friendly.
Thanks for your help ;)

---

### Post by sydbat on 2009-02-13
> **Amarus said:**
> Yeah I checked those bugs but it doesn't seem like the same problem. Same extensions are running on Vista with no problems but I'm gonna try using safemode to see if that helps. Maybe one of them isn't that *nix friendly.
Thanks for the help ;)Let us know what happens.

---

### Post by jou770d on 2009-02-13
> **sydbat said:**
> Let us know what happens.

This might be it, nothing wrong happened so far in the last 30+ minutes of using safe mode.
Tracking the culprit is not gonna be fun since this happens randomly and not always...
Thanks!

---

### Post by dandellion on 2009-02-13
Yesterday's update is killing me. 
OK, my FF is not crashing, but:
All the bookmarks have gone, restore function is not working and it refuses to save any new bookmark. 
It doesn't react on the home button. 
Each new tab is opened with last typed address in it (which is quite annoying). If the tab is opened via clicking the link, address will never be shown. 
Pages never show they have been loaded (circle in the icon's place rotates all the time)

How this thing managed to go through the official repositories?

---

