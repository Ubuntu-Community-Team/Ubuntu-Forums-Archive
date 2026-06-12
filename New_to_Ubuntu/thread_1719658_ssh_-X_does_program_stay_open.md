---
title: "ssh -X does program stay open?"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-04-02
I've been using ssh -X from a client to my server. I'm wondering what happens when I do that.

Does the program open on the server?
If I close the program on the client does it close on the server?
How do I closest when I'm done but keep it running, Im thinking of transmission.

---

### Post by gradinaruvasile on 2011-04-02
The program runs effectively on the other computer, but it transmits all graphical data to your X server. If you close it, it will close on the other computer.

If you are referring to the transmission bittorrent client, it has a web client you know.

But Deluge (it is in the repos) is better than Transmission and it has daemon, web interface and the option to connect to its daemon vis ssh tunneling from the preogram running on your computer - i did a test with this and works well, just make sure to have the same version on both computers otherwise it will work but wont send any feedback to you about the download status.
So install the daemon on the other computer (no need for graphical interface), start the gui on your computer, configure the connection to the other compuers daemon, start the downloads and then you can disconnect from it. There is a very good how to on their page.

---

### Post by nothingspecial on 2011-04-02
Try transmission-cli within screen

for example, ssh into your server

type ```
screen
```

Say you have a Ubuntu 10.10 torrent file in your home folder

```
transmissioncli -D -u 50 -er ubuntu-10.10-desktop-i386.iso.torrent
```

-D means no download limit

-u 50 means limit upload speed to 50kbs

-er means encryption required

type ```
transmissioncli -h
``` to see all the options

Then press Ctrl-D, this will detach your session and leave it running. You can logout of your server.

Next time you ssh in type screen -r and you will reattach your session.

---

### Post by wlraider70 on 2011-04-02
Great info in both thanks for the help. I'll test both solutions out.

---

