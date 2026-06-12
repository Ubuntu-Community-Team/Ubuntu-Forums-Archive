---
title: "xdg-open fails without a desktop environment"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-08-03
xdg-open fails to open folder without a proper desktop environment like gnome/kde.
I have openbox with thunar installed as file manager. When I run the command

```
xdg-open /tmp
```

then it shows the error

```
Warning: unknown mime-type for "/tmp" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
```

Searched the internet and found out that this is a bug. 
See bug report [here]("https://answers.launchpad.net/chromium-browser/+question/98720") and [here]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/220765").

Has this been solved yet?

---

### Post by Flimm on 2010-08-04
According to [that bug report](https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/220765), it's been [fixed upstream](http://bugs.freedesktop.org/show_bug.cgi?id=23280) but the fix hasn't been released in Ubuntu.

If you're comfortable compiling from source, you could do that with the upstream releases. Otherwise, wait for the new release to be packaged in Debian, then synced into Ubuntu. As we're past [DebianImportFreeze](https://wiki.ubuntu.com/MaverickReleaseSchedule), you're probably going to have to wait until maverick+1 unless a developer specifically syncs the fix over.

EDIT: seems like the fix hasn't been released upstream yet.

---

### Post by a.sarkar on 2010-08-04
@Flimm thanks for your answer.

Following your post, I found a simple yet effective solution. For people who would like a quick and simple hack, can do the following,  until xdg-open is fixed in Lucid (if at all). 
Install the package libfile-mimeinfo-perl.
```
sudo apt-get install libfile-mimeinfo-perl
```
Then copy the xdg-open to local home bin. 
```
cp /usr/bin/xdg-open ~/bin/
```
This would ensure your hack is not over-written by updates.
Finally open the ~/bin/xdg-open file and search for the open_generic() function and change the following lines
```
if which run-mailcap >/dev/null &&
```
to
```
if mimeopen -v 2>/dev/null 1>&2 &&
```
and the line
```
run-mailcap --action=view "$file"
```
to
```
mimeopen -n "$file"
```
Done. This works in openbox+thunar.

To set thunar as default folder opener 
```
mimeopen -d /tmp
```
The "-d" open sets the default application. For more options check 
```
mimeopen --help
```

---

### Post by Zalbor on 2010-08-22
Since copying xdg-open to your home directory makes this a per-user solution, why not just create an alias to gnome-open or kde-open, if you're using gnome or kde? I guess it depends on what you need xdg-open for.

In my case I just edited .bashrc and added this line near the end:
```
alias xdg-open='kde-open'
```

---

### Post by a.sarkar on 2010-08-22
@Zalbor

gnome and kde are desktop environments. As my subject line says "xdg-open fails without a desktop environment" so evidently I don't have a desktop environment like gnome/kde/xfce. In fact I am using openbox.

I found that xdg-open works with gnome without any hacks.

---

