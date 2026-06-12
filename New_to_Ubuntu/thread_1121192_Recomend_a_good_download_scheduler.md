---
title: "Recomend a good download scheduler"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-04-09
Hi,

I want a program that I can schedule to download large files (like Jaunty Jackalope.iso) from the internet (not via bittorrent) at midnight so I can use my isp's off peak time.

Preferably it would have a GUI and work with firefox and even do bittorrent too.

Is there such a program.  If not what is the next best thing?

---

### Post by The Cog on 2009-04-09
I would be inclined to use **wget**. It's more reliable than firefox. Launch it with **at** like this :
1: Say when to run: **at 2:00** (at warns about using sh)
2: Enter the command: **wget [http://www.acme.com/secret-file](http://www.acme.com/secret-file)**
3: End your command sequence with **Ctrl-D**

---

### Post by Captain_Glen on 2009-04-10
Isn't wget a command line program?

---

### Post by joeashcraft on 2009-04-10
wget is a command line program, yes. You can use gnome-schedule to create a crontab entry. I don't remember if gnome-schedule is installed by default. If you don't have it you can install it through synaptic. 
After installation it can be found under System > Preferences > Scheduled Tasks. Create new task by clicking the New button. Set the task description, execution time, and the task. The simplest task would be using wget (as The Cog suggested).

---

### Post by HermanAB on 2009-04-10
Actually, cron and wget have an excellent GUI: gedit.

---

### Post by joeashcraft on 2009-04-10
For general downloading, I like [axel]("http://packages.ubuntu.com/search?keywords=axel") (it's command line only, but you could use it from gnome-schedule if you wanted to). Axel is in the repo's and can be installed through synaptic. 

What makes axel different is it creates multiple connections to the server and downloads the file in parts. Theoretically this reduces your download time to 33% as long as you have enough bandwidth.

---

### Post by computermacgyver on 2009-04-10
I too think wget is your best bet, though it is a command line program.

If you really would like something with in firefox, look at the addon
[http://addons.mozilla.org](http://addons.mozilla.org)

---

### Post by The Cog on 2009-04-10
Yes, sorry, I don't know any GUI downloaders that you can automate.
At is kind of clunky though. It all happens behind the scenes. This mighe be better:
**sleep 2h 30m && wget [http://www.acme.com/secret-file](http://www.acme.com/secret-file)**
which you can do in screen if you want to disconnect and leave running. You can cancel it with Ctrl-C.

---

### Post by jjbarrows on 2009-08-22
"downloader for X" has a schedule option, and as the name suggest an X windowing GUI (with sound effects too!)

---

### Post by AClark on 2009-08-22
+1 for "Downloader for X"

Its under "d4x" in Synaptic

I've been using it to avoid the "Fair Access Policy" of my Satellite based ISP (300 meg per day) by scheduling podcast & ISO downloads from 2am to 6am when the FAP doesn't apply

It works for most urls but not all, for example the links for Cranky Geeks always fail and while Buzz Out Loud works every time The Buzz Report fails every time.

I haven't been able to find another GUI based downloader that allows scheduling but using cron & wget are worth a try.

---

