---
title: "how to download only selected 1 or 2 files with rtorrent?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-21
If someone knows, there is in the torrent 20 files.
I just need one specific, not all.

---

### Post by camaron1 on 2009-11-21
> **frenchn00b said:**
> If someone knows, there is in the torrent 20 files.
I just need one specific, not all.
What client are you using? 

Deluge and Ktorrent let you choose. When you click the torrent file you are given a list of all the files and you just tick or un-tick the ones you want

---

### Post by prshah on 2009-11-21
> **frenchn00b said:**
> If someone knows, there is in the torrent 20 files.
I just need one specific, not all.

In the main rtorrent screen, highlight (3 stars along the left) the torrent in question. Press right arrow key. Then scroll down (down arrow) to "Files" section. You will see a list of files. Press right arrow to select the filenames section, scroll the files list using up/down. press spacebar ONCE to turn "off" download of the particular file. Press spacebar TWICE to prioritize a particular file. The words "off" or "hig" will appear next to the filename to indicate it's status.

---

### Post by frenchn00b on 2009-11-21
> **camaron1 said:**
> What client are you using? 

Deluge and Ktorrent let you choose. When you click the torrent file you are given a list of all the files and you just tick or un-tick the ones you want

rtorrent
 [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by frenchn00b on 2009-11-21
> **prshah said:**
> In the main rtorrent screen, highlight (3 stars along the left) the torrent in question. Press right arrow key. Then scroll down (down arrow) to "Files" section. You will see a list of files. Press right arrow to select the filenames section, scroll the files list using up/down. press spacebar ONCE to turn "off" download of the particular file. Press spacebar TWICE to prioritize a particular file.

wow !! that s nice. 

I thank you very much !!!

---

### Post by frenchn00b on 2009-11-21
> **prshah said:**
> In the main rtorrent screen, highlight (3 stars along the left) the torrent in question. Press right arrow key. Then scroll down (down arrow) to "Files" section. You will see a list of files. Press right arrow to select the filenames section, scroll the files list using up/down. press spacebar ONCE to turn "off" download of the particular file. Press spacebar TWICE to prioritize a particular file. The words "off" or "hig" will appear next to the filename to indicate it's status.

btw please while it is downloading would you know how to add a 
*.torrent file that is located into my /tmp ?

---

### Post by prshah on 2009-11-21
> **frenchn00b said:**
> btw please while it is downloading would you know how to add a 
*.torrent file that is located into my /tmp ?

From the main rtorrent screen, press Enter. This will prompt for a torrent file name. Enter the entire file name, or use [tab-completion]("http://en.wikipedia.org/wiki/Command_line_completion"). It will be added to the list. Then select it (3 stars along the left) and press Ctrl+S to start the download. 

If you use backspace instead of Enter, it will add the file and start the download automatically (ie, no need to select and press Ctrl+S).

If you do not understand the link about tab-completion, please post back for an explanation.

---

### Post by frenchn00b on 2009-11-21
> **prshah said:**
> From the main rtorrent screen, press Enter. This will prompt for a torrent file name. Enter the entire file name, or use [tab-completion]("http://en.wikipedia.org/wiki/Command_line_completion"). It will be added to the list. Then select it (3 stars along the left) and press Ctrl+S to start the download. 

If you use backspace instead of Enter, it will add the file and start the download automatically (ie, no need to select and press Ctrl+S).

If you do not understand the link about tab-completion, please post back for an explanation.

thanks a lot. You are the kind of rtorrent! It helped a lot!! it works

---

### Post by prshah on 2009-11-21
> **frenchn00b said:**
> You are the kind of rtorrent!

Heh, I think you mean king :)

I _love_ rtorrent. I've tried uTorrent, Deluge, Transmission, Azure (?) and about a quarter-dozen others; rtorrent is the best!

I especially like it that I can SSH to my box anytime and control rtorrent; remote control via VNC is difficult and practically impossible when a torrent client is gobbling up all the bandwith!

Once you get more familiar with rtorrent, you really should look into customizing it... here's a few things you can do with it:

a) Automatically load and start torrent files from a specific directory.
b) Move completed torrents to another directory.
c) "Tie" torrents to a directory, so that if you delete the original torrent file, the download is automatically stopped.
d) Use a session directory to automatically load and start torrents from where you have quit the last time.
e) Use MULTIPLE rtorrents!

... and so on.

---

### Post by frenchn00b on 2009-11-21
> **prshah said:**
> Heh, I think you mean king :)

I _love_ rtorrent. I've tried uTorrent, Deluge, Transmission, Azure (?) and about a quarter-dozen others; rtorrent is the best!

I especially like it that I can SSH to my box anytime and control rtorrent; remote control via VNC is difficult and practically impossible when a torrent client is gobbling up all the bandwith!

Once you get more familiar with rtorrent, you really should look into customizing it... here's a few things you can do with it:

a) Automatically load and start torrent files from a specific directory.
b) Move completed torrents to another directory.
c) "Tie" torrents to a directory, so that if you delete the original torrent file, the download is automatically stopped.
d) Use a session directory to automatically load and start torrents from where you have quit the last time.
e) Use MULTIPLE rtorrents!

... and so on.

script to get url, but stil dont know how to import it.
```
CODEE="1"

##read CODEE

while [ "$CODEE" != ""  ] ; do

printf "THE URL :> "
read CODEE
echo "$CODEE"

printf "To which name:> "
read TO

echo "$TO"


wget "$CODEE" -O "$TO"

ls
echo " "
done

```


I use this config.
 [http://www.linuxquestions.org/questions/ubuntu-63/how-to-install-and-optimize-rtorrent-552280/?](http://www.linuxquestions.org/questions/ubuntu-63/how-to-install-and-optimize-rtorrent-552280/?)


b) Move completed torrents to another directory.
that line didnt work
```
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/frechn00b/rtorrent/downloading/ ;d.set_directory=/home/frechn00b/rtorrent/downloaded/"
```

---

