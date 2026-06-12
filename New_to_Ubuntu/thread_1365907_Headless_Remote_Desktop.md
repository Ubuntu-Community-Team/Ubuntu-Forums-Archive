---
title: "Headless Remote Desktop?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by BT1 on 2009-12-27
I would like to set up a type of local server type...thing... where it stays on without a monitor, but I want to do remote desktop type "browsing" so to speak when using it. I have never used remote desktop type stuff before, so I don't know if it will be a little window on my desktop or what. 

My end goal is to run virtual box on this...box, and use VMs through remote desktop.

Do I need to have a "Desktop Manager" installed in order to run remote desktop?

---

### Post by aktiwers on 2009-12-29
In terminal you can simply open it in fullscreen by typing:
```
rdesktop -f THEIPOFYOURSERVER:PORT
```

---

### Post by tad1073 on 2009-12-29
if your user is not logged in on the server and remote desktop is not turned on you will not be able to use rdesktop.

you can ssh with an x-session

```
ssh -X user@serveripaddress
```

open a file browser with

```
gksu nautilus
```

---

### Post by spiky001 on 2009-12-30
i have that set up i use the remote desktop viewer,On server go to system/pref/ remote desktop set your settings to allow you access your good to go. You might want to put a firewall on server to allow only your connection hope this helps

---

