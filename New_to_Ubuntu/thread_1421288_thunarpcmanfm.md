---
title: "thunar/pcmanfm"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by dzon65 on 2010-03-04
Does anyone know how to replace xfce's thunar with pcmanfm or rox?

---

### Post by kerry_s on 2010-03-04
personally i think thunar's better, but it's basically what you did with the panel.

killall thunar && pcmanfm -d &


make sure you turn on the save session on logout in the xfce4 session so it saves everything for every start.

---

### Post by dzon65 on 2010-03-04
Kerry.I was actually just curious.I still haven't figured out how to add url shortcuts to the ADeskbar.So for now got some desktop icons.Thunar can't handle the desktop.It's just when everything's set to open on a single click,doubleclicking desktop icons is weird.But like I said,it's just temporary.Btw,check out the lxpanel.

---

### Post by kerry_s on 2010-03-04
> **dzon65 said:**
> Kerry.I was actually just curious.I still haven't figured out how to add url shortcuts to the ADeskbar.So for now got some desktop icons.Thunar can't handle the desktop.It's just when everything's set to open on a single click,doubleclicking desktop icons is weird.But like I said,it's just temporary.Btw,check out the lxpanel.

yeah, sorry forgot xfdesktop handles the desktop icons, make sure you kill that if your going to have pcmanfm manage it.

i'm not familiar with adeskbar, but if it's like any other launcher i suppose you would do like " firefox [http://www.google.com/](http://www.google.com/) " for example i use chrome so it would be " google-chrome [http://www.google.com/](http://www.google.com/) ".

your setup looks very nice, looks like your starting to find your place. just stick to it, take your time, things get easier. everyone hops around, everyone tries different things, till you find what just works for you. i'm lazier these days & don't do much tweaking on the desktop, as long as it works i'm happy.

i use gnome on my nettop, standard 1.6ghz atom 1gb ram, it was a barebone from newegg, [http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011) it was $86 when i bought mine, so it was less then $100 dollars to put together, since i had ram & hd.

anyways this is how simple mine looks, i like the old blue & grey colors like windows.

---

### Post by dzon65 on 2010-03-04
ADeskbar is one of the lightest docks.It's standard on madbox slitaz/madbox xfce.It's a simple thing but does exactly what it's supposed to do.You can have a media file browser with it if necesarry.I just don't know how to add them url's.It's different than other commands (or I must be doing something wrong).
As for the tweaks,well,always looking for lightweight solutions.Tried several distros but always back to minimal.This one's nice.xfce4,thunar,openbox,gpic,mirage,lx panel,roxterm,mplayer,abiword,gnumeric.....For now this loads <2Gb and is really fast.I have the exact setup on an old 512mb ram,nvidia vanta,10Gb HD,13 years old compaq and it works really well.Btw,can't seem to add url-shortcuts to the lx panel,exept for FF,as well.Strange,I use the exact commands used by the desktop icons.

[http://www.youtube.com/watch?v=LtQFJa1f0E0](http://www.youtube.com/watch?v=LtQFJa1f0E0)

---

### Post by kerry_s on 2010-03-04
dang, madbox looks nice. thanks!
i was going to try the adeskbar, but it's not in the jaunty repo's.

---

### Post by dzon65 on 2010-03-04
Here you go man! It comes in deb format:[http://crunchbanglinux.org/forums/topic/441/little-application-launcher-for-openbox/](http://crunchbanglinux.org/forums/topic/441/little-application-launcher-for-openbox/)

---

### Post by kerry_s on 2010-03-04
> **dzon65 said:**
> Here you go man! It comes in deb format:[http://crunchbanglinux.org/forums/topic/441/little-application-launcher-for-openbox/](http://crunchbanglinux.org/forums/topic/441/little-application-launcher-for-openbox/)

yeah, i got it from here-> [http://www.ad-comp.be/public/projets/ADeskBar/deb/](http://www.ad-comp.be/public/projets/ADeskBar/deb/)

just getting it setup, moving things around. still learning it.

---

### Post by dzon65 on 2010-03-04
It's about the lightest you'll find.IMOH it's perfect for the job.No idea how much that media filer takes but can't be much.Don't need those,almost movie like features,in awn or cairo.Say,gimme a whistle when you manage to get those url's going.

---

### Post by kerry_s on 2010-03-04
> Say,gimme a whistle when you manage to get those url's going.

i'm not sure what you mean by "url's", are you talking folders or web sites?

folders = your-file-manager /path/to/folder
web = your-web-browser [http://some-site.com/](http://some-site.com/)

i'm looking into the plugins, man they need some docs. :)

---

### Post by dzon65 on 2010-03-05
Yeah,my bad.So I ment website shortcuts.It's strange,for example when I add firefox to the bar,it'll open FF but won't connect (server not found).Other website links do nothing.Had this once before,had to add something to the command,but can't remember.Oh well,I'll figure it out.

---

### Post by kerry_s on 2010-03-05
do "man firefox" or "firefox --help" to see what the commands are.
sorry, i don't have firefox installed, i use epiphany or chrome.

---

### Post by dzon65 on 2010-03-05
Every time I add a website shortcut,adeskbar crashes and it can't be reopened.AAAAARRRRGGGHHH!!!!

---

### Post by dzon65 on 2010-03-05
Well Kerry,don't know if it works for you but Ijust cannot add website shortcuts to adeskbar launchers.When I do,it just crashes.The only one I could add is FF.All systemlaunchers do work however.I'll start another thread on this.

---

### Post by kerry_s on 2010-03-05
> **dzon65 said:**
> Every time I add a website shortcut,adeskbar crashes and it can't be reopened.AAAAARRRRGGGHHH!!!!

yeap, your right it crashed. did the same to me.

---

### Post by kerry_s on 2010-03-05
i had to get rid of adeskbar, it caused gnome to focus all new applications in the background, which annoyed the hell out of me.
no big loss though, i can get the same look with gnome panels set to autohide & it's easy drag & drop to add programs, just had to tweak the speed so the hiding is instant.

---

### Post by dzon65 on 2010-03-06
Yeah,I'll get rid of it as well.Can't seem to dowhat I want.Tried wbar,just the same.When I had thatminimal gnome setup,did the autohiding as well,can be annoying when minimizing,maximizing windows though.One of the things keeping me from lxpanel is the fact that you cannot add website shortcuts to it.Installed lxde on the old one.Gonna try to replace the lxpanel with the gnome one,in the lightest possible way.I know,it's working backwards,but trying to find a compromise between speed and functionality.

---

### Post by dzon65 on 2010-03-06
Kerry,check this one.I think this could make a good and light setup.Lxde,thunar (instead of pcmanfm) and gnome panel.I found the cpu part intresting.
[http://ubuntuforums.org/showthread.php?t=1269788](http://ubuntuforums.org/showthread.php?t=1269788)

---

### Post by kerry_s on 2010-03-06
i'm pretty much satisfied with my lxde install. i just been messing around with gnome, i added maximus & switched epiphany for arora, i'm using the ppa version, it's qt but feels faster then google chrome, i might just make it my main browser.

---

### Post by dzon65 on 2010-03-06
yeah,starting to like lxde as well.Didn't at first (used to ubuntu lite)but I like it better than xfce.Ditched pcman though.Prefer thunar.And replacing lxpanel in a few minutesFF runs pretty well but would like to give swiftfox a run.From what I've seen,loading is faster aaand it supports the same addons.(must have stylish).

---

### Post by dzon65 on 2010-03-06
Just replaced the lx with gnome.Indeed,there's hardly any difference in ram.

---

### Post by kerry_s on 2010-03-06
turn on reduced resources & turn off animations in gconf editor, it will be even more lighter. give arora a try for web browser, far less bloat.

---

### Post by dzon65 on 2010-03-07
Arora is really fast.One question,how do I make it "follow" the set gtk theme?

---

### Post by kerry_s on 2010-03-07
> **dzon65 said:**
> Arora is really fast.One question,how do I make it "follow" the set gtk theme?

you should have qtconfig installed with arora make sure it's set to default setup.

are you using the ppa version? it's more stable.

```
deb http://ppa.launchpad.net/mapopa/arora-stable/ubuntu jaunty main
```

change "jaunty" to what your using. you might need the key to:

[https://launchpad.net/~mapopa/+archive/arora-stable](https://launchpad.net/~mapopa/+archive/arora-stable)

---

### Post by dzon65 on 2010-03-07
Ok,done.Works well.Kerry,one more question.How did you install lxde?Posted a thread on this.
[http://ubuntuforums.org/showthread.php?t=1423746](http://ubuntuforums.org/showthread.php?t=1423746)

---

### Post by kerry_s on 2010-03-07
> **dzon65 said:**
> Ok,done.Works well.Kerry,one more question.How did you install lxde?Posted a thread on this.
[http://ubuntuforums.org/showthread.php?t=1423746](http://ubuntuforums.org/showthread.php?t=1423746)

i use debian lxde, installed with the net installer. when you boot it select advanced-> other desktops-> lxde

---

