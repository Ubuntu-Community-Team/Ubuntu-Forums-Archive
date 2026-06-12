---
title: "Not sure if i can get any help here (regarding ssh)"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Spacedementia87 on 2007-09-27
At my university we have a daily internet traffic limit for my halls, however we have been told that in linux using ssh we can connect directly to the department connection using ssh and so bypass the traffic limit.

So i set up the ssh tunnel:

```
jajh2@jajh2:~$ ssh -D port address
jajh2@address's password: 

```

and it connects giving me the message of the day.

So then i set up my socks 5 proxy (as the university officials say in the guide) on firefox and thunderbird. and i assume they work.  (at some point i will download a large file to check my bandwidth usage)

Now i come to Azureus.  I set up the socks 5 settings in the options tab and restart.  then the terminal reports this:

```
jajh2@soup:~> channel 8: open failed: connect failed: Connection refused
channel 8: open failed: administratively prohibited: open failed
```

and then continues to download ignoring the ssh tunnel (the limit still counts)

My guess is that the administration have set up a system not allowing azureus to connect through the ssh tunnel.

If i am wrong on my assumption and you can think of a way to fix it, please let me know.


Also a quicky, how can i write the ssh tunnel set up as a start up script?  Can't seem to get it to work.

---

### Post by Spacedementia87 on 2007-09-28
any help?

---

### Post by fuhrysteve on 2008-03-31
I have heard reports of
```
chanel x: open failed: administratively prohibited: open failed
```
being a result of either using SOCKS4 instead of SOCKS5, and also accessing the proxy from localhost instead of 127.0.0.1. I get this error all the time with SOCKS5, but I have never found that it is actually problematic -- in other words, my requests appear to get through regardless of the error.

As for running Azureus via SOCKS, try bypassing the connection settings by opening azureus with tsocks
```
sudo apt-get install tsocks
```
like this:
```
tsocks azureus
```

You may have to edit the settings in
```
sudo gedit /etc/tsocks.conf
```
However, I believe you won't even need to do that if you broadcast your SOCKS proxy from the usual SOCKS port 1080, which is the default port for tsocks, if I am not mistaken.

At any rate, for performance reasons I'd strongly advise using ktorrent, a utorrent (for M$ win) clone instead of Azureus.
```
sudo apt-get install ktorrent
```
or even better,[ rtorrent]("http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide"), which is completely console (text) based, behind screen,
```
sudo apt-get install rtorrent screen
```
rtorrent gets unparalleled performance.

To run these through a SOCKS proxy is the same principal as before. Start them like so:
```
tsocks ktorrent
```
```
tsocks rtorrent
```

Though I find it more convenient to just use [sshmenu]("http://sshmenu.sourceforge.net/") (puts a little menu for SSH connections on your panel) or [gSTM]("http://sourceforge.net/projects/gstm/") (SSH tunnel manager.. it has an autostart option, so I assume it will start it for you on bootup). It sounds to me like you want gSTM if you want your bittorrent client to automatically start downloading via SOCKS at startup:

You'll have to figure out how to make your bittorrent client start behind tsocks at startup (not sure offhand). Getting [rtorrent to start automatically behind a screen at bootup]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#StartingrTorrentonSystemStartup") is VERY rewarding, but may be a bit of a pain on some systems.

---

