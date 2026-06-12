---
title: "tomboy does not update"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-30
I did "sudo apt-get install tomboy"
and I got
[quote]Reading package lists... Done
Building dependency tree       
Reading state information... Done
_**tomboy is already the newest version.**_
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. [\QUOTE]

But I see here: [http://projects.gnome.org/tomboy/download.html](http://projects.gnome.org/tomboy/download.html)
that 1.0.1 is the newest stable version (1.1.0 is the newest development version). Mine is 1.0.0 
( I did a "sudo apt-get update" before running the above command)

---

### Post by avdzm on 2009-11-30
Hey,
I found this, add this to your software sources.
[https://launchpad.net/~tomboy-packagers/+archive/stable](https://launchpad.net/~tomboy-packagers/+archive/stable)

---

### Post by avdzm on 2009-11-30
U might also like to have a look at this page...
[https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes](https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes)

---

### Post by iRounak on 2009-11-30
> I found this, add this to your software sources.
[https://launchpad.net/~tomboy-packagers/+archive/stable]("https://launchpad.net/%7Etomboy-packagers/+archive/stable")How do I do it? APT line dialog box "Add Source" button is disabled/faded when I paste the above url.
[http://dl.dropbox.com/u/872430/Files%20Shared%20from%20GNOME%20Do/Screenshot-Untitled%20Window-2119789752.png](http://dl.dropbox.com/u/872430/Files%20Shared%20from%20GNOME%20Do/Screenshot-Untitled%20Window-2119789752.png)

---

### Post by avdzm on 2009-12-01
Open that link with firefox the apt links r in there.
In the page there is a combo box, make sure u select ur distro.
It will then show u the apt links.

---

### Post by iRounak on 2009-12-01
Thanks. It did work. I updated tomboy with the command
sudo apt-get install tomboy
So far, I had a habit of installing new softwares using 
"sudo apt-get install softwarename".
Do I have to add their ppa line to Software sources to update them. Is there an easy way to find their ppa line?

---

### Post by avdzm on 2009-12-01
To update tomboy, you need to type this command,
```
sudo apt-get update tomboy
```

---

### Post by iRounak on 2009-12-01
Actually, 
> sudo apt-get update tomboy

E: The update command takes no arguments


But that is not the question that I asked now. As I said, I have updated it using "sudo apt-get install tomboy"

---

### Post by avdzm on 2009-12-01
Ah, I reread ur post.
Usually for third parties software you need to add their ppa to get their updates.

---

### Post by iRounak on 2009-12-01
> Usually for third parties software you need to add their ppa to get their updates.
Would using Synaptic help or will I still have to add PPA to get updates?

---

### Post by avdzm on 2009-12-01
Synaptic can show u a list of all the updates, but u still have to add third party ppa to get them.

---

### Post by javakinetic on 2010-05-27
[B]THIS TOOK FOREVER TO FIND

ppa:tomboy-packagers/development

Add that to your software sources... and hit upgrade

Spirce:  [https://launchpad.net/~tomboy-packagers/+archive/development](https://launchpad.net/~tomboy-packagers/+archive/development)
[/B]

---

