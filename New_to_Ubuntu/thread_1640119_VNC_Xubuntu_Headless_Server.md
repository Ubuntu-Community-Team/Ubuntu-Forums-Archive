---
title: "VNC Xubuntu Headless Server"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by TheVillain9 on 2010-12-07
I've got a file/media server running on my ubuntu server. I installed the xubuntu on top initially, so i could setup things initially and learn.

I now want to make the server headless(ie. no monitor, keyboard or mouse). I want to now have the server boot to terminal, but logged in as my main user. I need the ability to vnc in, but i want to vnc in as the user logged on and will never logon as another user.

I'm not sure about how to change the booting not to load the gui, get it autologin and start the vnc server. Secondly not sure which vnc server(vnc4server,tightvnc,x11nvc) i need setup, since i want to logon as the user that was booted up as. Lastly i've read a lot of other posts, that using SSH would be more secure. Where does that fall in?

Thanks for the help. I've been reading a lot of posts, but its been tough to tie it altogether.

---

### Post by cariboo on 2010-12-07
You've got your terminology a bit wrong, but it's fairly easy to do what you want, except for the auto login in a console.

Depending on which Desktop Manager you are using,  you have to purge it. The first thing to do ist go to a console, Ctrl-Alt-F1, then login and stop the the DM. If you are using Lucid or newer:

```
sudo service gdm stop
```

if you are using XDM:

```
sudo service xdm stop
```

Previous to Lucid (10.04) use:

```
sudo /etc/init.d/gdm stop
```

Once you have stopped the DM, you can purge it:

```
sudo apt-get purge gdm
```

Once you have done this, you can still get to the gui desktop by typing:

```
startx
```

at the prompt.

To access the system remotely, I would suggest using ssh, the client is installed by default on all versions. On your server you need to install the server:

```
sudo apt-get install openssh-server
```

for more info on setting up the ssh server have a look [here. ]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") Once you have ssh setup, you can use xforwarding to run gui apps on you desktop:

```
ssh -X user@server
```

then once at the prompt type the name of the application you want to use for example nautilus, the file manager:

```
nautilus
```

---

### Post by cariboo on 2010-12-07
You've got your terminology a bit wrong, but it's fairly easy to do what you want, except for the auto login in a console.

Depending on which Desktop Manager you are using,  you have to purge it. The first thing to do ist go to a console, Ctrl-Alt-F1, the login and stop the the DM. If you are using Lucid or newer:

```
sudo service gdm stop
```

if you are suing GDM, for XDM:

```
sudo service xdm stop
```

Previous to Lucid (10.04) use:

```
sudo /etc/init.d/gdm stop
```

Once you have stopped the DM, you can purge it:

```
sudo apt-get purge gdm
```

Once you have done this, you can still get to the gui desktop by typing:

```
startx
```

at the prompt.

To access the system remotely, I would suggest using ssh, the client is installed by default on all versions. On your server you need to install the server:

```
sudo apt-get install openssh-server
```

for more info on setting up the ssh server have a look [here. ]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") Once you have ssh setup, you can use xforwarding to run gui apps on you desktop:

```
ssh -X user@server
```

then at the prompt type the name of the application you want to use for example nautilus, the file manager:

```
nautilus
```

---

### Post by TheVillain9 on 2010-12-10
when i do startx, it logs into gnome. any ideas on how i could log into xubuntu, which i guess is just really xfce. thanks.

---

