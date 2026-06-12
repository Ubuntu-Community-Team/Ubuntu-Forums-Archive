---
title: "torrents"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by shadowlands on 2009-04-19
just talking out loud. which torrents work on ubuntu? I have seen a couple listed on here and if someone might want to use one just talking out loud how do you install them?

---

### Post by Svensk023 on 2009-04-19
do you mean which torent clients work?

Ubuntu comes with transmission 

but I use Deluge, you can get it through the Add/Remove app function.

and all you have to do is download the small .torrent file and open them up through your client to start the download.

---

### Post by shadowlands on 2009-04-19
say some one is very green and wish to use a client. is there step by step direction to making them work.  

just talking out loud what is Deluge and how might one install it?

---

### Post by anjilslaire on 2009-04-19
Also there is ktorrent
```

sudo apt-get install ktorrent

```

---

### Post by SuperSonic4 on 2009-04-19
I get deluge via a deb on their site because it takes ages for the repo version to update

edit: seems they have a PPA: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by AndyCooll on 2009-04-19
If you are as green as you say, forget Deluge for a moment (you can always come back to trying different torrent downloading clients later). Transmission is already installed by default.

What you need to do to download a torrent is first get hold of the "torrent seed" for the file you wish to download. A torrent seed is a small file containing information about other clients that have copies of the file you wish to download. For instance you download Ubuntu via a torrent.

Next open up Transmission (Applications > Internet > Transmission BitTorrent Client). Then click on "Add" and navigate to the "torrent seed" you downloaded earlier. That's it, the file should now begin to download. By default it will start downloading to your desktop. You can change this in Transmission by selecting Edit > Preferences and choosing a different destination folder.

:cool:

---

### Post by Tibuda on 2009-04-19
> **shadowlands said:**
> say some one is very green and wish to use a client. is there step by step direction to making them work.
To work with Transmission.
[LIST=1]
[*]Click Applications.
[*]Click Internet.
[*]Click Transmission.
[*]Click the Torrent menu.
[*]Click Add.
[*]Choose you torrent file.
[/LIST]
Or just double-click you torrent file.

You can find torrent files in many torrent search engines like mininova and piratebay (piratebay still works after that trial?)

---

### Post by shadowlands on 2009-04-19
ok  but what if someone ried and a program called mirror  comes up?

---

### Post by shadowlands on 2009-04-19
miro program comes up.
what am i to do?

---

### Post by shadowlands on 2009-04-19
Lost when it comes to direction number 4.

> **danielrmt said:**
> To work with Transmission.
[LIST=1]
[*]Click Applications.
[*]Click Internet.
[*]Click Transmission.
[*]Click the Torrent menu.
[*]Click Add.
[*]Choose you torrent file.
[/LIST]
Or just double-click you torrent file.

You can find torrent files in many torrent search engines like mininova and piratebay (piratebay still works after that trial?)

---

### Post by steve101101 on 2009-04-19
in the program transmission. click the menu button named torrent then click add. then all you have to do is to find and open the torrent file you have already downloaded.

---

### Post by steve101101 on 2009-04-19
here is some general info on torrents so that you can understand the system better. [http://netforbeginners.about.com/od/peersharing/a/torrenthandbook_3.htm](http://netforbeginners.about.com/od/peersharing/a/torrenthandbook_3.htm)

---

### Post by cariboo on 2009-04-19
Using transmission is pretty easy, go to a web site that has torrent links, like [this]("http://releases.ubuntu.com/releases/9.04/") and click on the link ending with torrent. Transmission will automatically open and ask you where you want to save the file, select the destination and click add. The main transmission window will open and the file will start downloading.

Jim

---

### Post by shadowlands on 2009-04-19
The thing is when something works it is like poof it works and green horns have no clue as to how and most times do not care how it works as long as it works.

This makes trouble shooting very hard.

---

### Post by shadowlands on 2009-04-19
> **cariboo907 said:**
> Using transmission is pretty easy, go to a web site that has torrent links, like [this]("http://releases.ubuntu.com/releases/9.04/") and click on the link ending with torrent. Transmission will automatically open and ask you where you want to save the file, select the destination and click add. The main transmission window will open and the file will start downloading.

Jim

will ktorrent do the samething.

---

### Post by lovinglinux on 2009-04-19
> **shadowlands said:**
> miro program comes up.
what am i to do?

You need to configure Firefox to load .torrent files with Transmission or any other client, assuming that you don't want to use Miro. Open Firefox "Preferences", click the "Applications" tab, then select the option "BitTorrent seed file" under the "Content type" column, then click the drop-down menu in the "Action" column and select "Transmission". If the application you want is not listed, then you can use the browse button to find it. It will probably be under /bin directory.

Miro also can download torrents, but I don't like it. I personally recommend Deluge, but since you are green, I recommend a little extension for Firefox called [firetorrent](http://www.fireaddons.com/downloads/).

Simply download firetorrent form [this link](http://www.fireaddons.com/downloads/). It should install automatically, then restart Firefox, find a torrent to download and click it. It should start downloading the file automatically by the built-in Firefox download manager, like any other regular download. Can get simpler than that.

You might need to open the torrent port on your router to accept connections. I don't remember exactly, but I guess Firetorrent uses port 6881. If you decide to use Transmission or Deluge, then you can configure your own port number.

---

### Post by anjilslaire on 2009-04-20
> **shadowlands said:**
> will ktorrent do the samething.

Yes, all torrent clients work essentially the same, with a few different features each.

---

### Post by shadowlands on 2009-04-20
I have ktorrent on my acer 5570z and I added the Firefox to load .torrent files and now my computer freezes up. icons disapear and turn in to squares with red "x"s in them. the only thing I can do is take the battery out to turn it off.  The computer is very slow also.

---

