---
title: "VNC Questions"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Onay on 2007-10-30
I'm getting a bit frustrated since people seem to expect me to know more than I do. I have never done anything related to remote desktop usage, and I really don't understand many of these things...

1. How can I find out my IP address? According to random websites in a search in google, it is different from each site.
2. How can I open up ports? I have firestarter and I've tried opening up port 5500 and I still cannot connect to the other machine.
3. Do I need to download any other packages in order to connect?
4. If I use this only for a few minutes every once in a while (for help purposes) do I really need to connect securely?

---

### Post by elspiko on 2007-10-31
1. Type in ```
ifconfig
``` in a terminal. It will show you your address settings for all network interfaces on your machine.

2. Might not have to.

3. In a word yes. If your connecting TO a Ubuntu/Debian machine (possibly others), then the server side application is already installed. Go to System -> Preferences -> Remote Desktop.

Under sharing, depending on whether you want to control or view, select the relevant boxes.
Under security, tick 'Require the user to enter a password' and enter the password Then click close.

If the remote desktop option isn't there...

```
sudo apt-get install vino
```

On the client (machine your connecting from), you'll need VNC Viewer. For Windows you can get a free version from [http://realvnc.com](http://realvnc.com)

If your viewing from Ubuntu et al., you'll need to install the vnc viewer

```
sudo apt-get install vncviewer
```

You then run Vnc

Windows (Start - All Progs - Real VNC - VNC Viewer 4 - Run Vnc Viewer) + enter the DNS/IP Address of the machine your connecting TO + the password.

Ubuntu
```
vncviewer ipaddress or computername:0
```

As for security, its possible to run VNC over ssh, Google it or Search on these forums

Hope this helps

---

### Post by Onay on 2007-11-01
I did all of those and I still get an error message, though it is different than ones in the past. It does not say that "it cannot find the host", but now it just has a "timed out connection". That means that the other person was found, but it cant connect.

The other machine is connected to the internet via a protected internet connection on a college campus. Ports 5500, 5900, and 5901 are open, but do you think that there is something else that needs to be unlocked for me to connect?

---

