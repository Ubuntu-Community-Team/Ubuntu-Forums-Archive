---
title: "[SOLVED] XP laptop running TightNVC to ubuntu desktop? possible?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by ijason on 2008-12-05
hey there. this is somewhat of a continuation of my earlier thread, here : [http://ubuntuforums.org/showthread.php?t=992090](http://ubuntuforums.org/showthread.php?t=992090)

but now i've solved the ping issues, and still am unable to get the remote-desktop to work! any help would be really appreciated.

i've got a dell laptop running XP, with TightVNC installed. and i've got a desktop running ubuntu and i'd really like to be able to use the default remote-desktop application that you can enable in your preferences. but if i need to install a third party, that's fine too. 

i can ping the desktop from the laptop, and the laptop from the desktop. so far so good. however, when i put in the IP for the desktop i get the error "failed to connect to server". and when i put in 'jason-desktop' for the address i get the error "failed to get server address".

any suggestions?? is there a way to watch from the ubuntu machine to see the requests coming in?

---

### Post by cariboo on 2008-12-05
I would suggest using tightvncserver on your Ubuntu desktop. Tightvncserver is in the repositories, you can use Synaptic or the command line to install it.

JIm

---

### Post by halitech on 2008-12-05
look at this thread, seems there are some good instructions on setting up what you are looking for

[http://ubuntuforums.org/showthread.php?t=941530&highlight=remote+desktop](http://ubuntuforums.org/showthread.php?t=941530&highlight=remote+desktop)

---

### Post by ijason on 2008-12-05
@cariboo :

i've already installed tightvncserver from the repo's, and initiated it simply with the command "tightvncserver" from a command prompt. 

this gets me "New 'x' desktop is jason-desktop:1" which seems like it's been successful, but i get the same error messages from tightvnc when i try to connect to my desktop's IP. 

??

---

### Post by nhasian on 2008-12-05
i have ultravnc installed on my windowsXP machine and i can log into my ubuntu machine without installing anything extra.  Just make sure in your ubuntu machine you enable remote login by going to

System -> Preferences -> Remote Desktop and you have checked *Allow other users to view your desktop* and *Allow other users to control your desktop* also click on *Require the user to enter this password*

thats all you need to do on the ubuntu side to make it work.

---

### Post by ijason on 2008-12-05
@hali : that does look like a very friendly tutorial on using NX, which i've looked into. but it doesn't quite explain the angle of getting my XP laptop to talk to an ubuntu machine. i'll read more thoroughly through it later today though - i hope to have an ubuntu netbook by the end of the year and that link will no-doubt come in very handy.

---

### Post by ijason on 2008-12-05
@ nhasian : is ulravnc (do you mean ultravnc? i haven't heard of either) much different than tightvnc? i'm not particularly loyal to tight, it's just the one that was recommended to me :)

tell me this, what address do you type into the viewer-side? is it the local ip of your server machine, or is it more like 'jason-server'? do you need to put any extra numbers to define which x-session you'll be viewing?

it sounds like exactly what i'd hoped i could do : simply enable desktop sharing on the ubuntu box and throw in the password i want to require and be done with it.

---

### Post by nhasian on 2008-12-05
yes its UltraVNC.  i fixed the typo.  I usually use the IP address to connect like 192.168.1.105:5900 but I tested it with the hostname hpnhasian:5900 and it worked too ):P

PS You can also connect to your Ubuntu machine from your iPhone with VNClite

---

### Post by ijason on 2008-12-05
@nhasian : ok... i've downloaded and installed ultravnc, and i went ahead and killed the tightvncserver process that i had started on my desktop. i have the remote-desktop option enabled as suggested earlier in this thread. 

when i try to connect to 192.168.1.4:5900, i get "failed to connect to server" as the error message. :(

i know that this is the address of the ubuntu machine from ifconfig, and i can successfully ping it from my laptop. i wish the error message gave me more info!

i do have 'allow only local connections' checked on the desktop. just because this is not an encrypted channel so i only want people on my router to be able to log on. could that be causing the problem?

---

### Post by cdmike2k8 on 2008-12-05
I have a vnc setup, but I am going ubuntu to ubuntu.  The one important part that seems missing is what vnc desktop you are connecting to.  Using vncviewer, I would use ```
vncviewer 192.168.1.4:5901 
```  Its 5901 because the last digit is the desktop number.  Also, I need to start the vnc session, so on the server(desktop) I use command ```
vncserver
```  Try using this at first, and then you could install ssh to get in at command line to start vnc session if one is not going.  Just my 2 cents.
EDIT:
Try connecting with allow local unchecked if it doesn't work with it checked

---

### Post by ijason on 2008-12-05
@ cdmike : yeah, it seems like it will be drastically easier to remote-desktop when both machines are running ubuntu. in fact, the remote-desktop application that comes pre-installed with ubuntu describes exactly what you said. "simply type vncviewer jason-desktop:0". confounded windows! :)

i tried your advice about upping the port to 5901 to account for the x-session. but still getting the same error. i'll try turning off the local-connection limitation. although, surely it understands anything from the same DNS server is local.

---

### Post by ijason on 2008-12-05
ha! well, turning off the 'local connections only' option let it work right off the bat. using port 5900, too.

i wonder what crazy definitions it has for "local" if it's not letting a machine from the same network connect?

thanks :)

---

### Post by cdmike2k8 on 2008-12-05
Well, at least we fixed it.  Would you want it accessible outside your network?  I have mine like that and I really like it, especially since I am away from that machine by about 300 miles.

---

### Post by juanoleso on 2008-12-05
"local connections only" makes a lot of sense.  That means only connections to the local loop "127.0.0.1" are accepted.  I have my ubuntu box at home setup so that I SSH into it and then I have a tunnel setup to the vnc port.  It acts as a local connection at that point.  Connection from tightVNC to the ubuntu box directly (not through an SSH or telnet tunnel) means that it is not a local connection.

---

### Post by ijason on 2008-12-05
@ juan : aaah. that's a different kind of "local" connection than i was thinking. so you essentially log onto the machine via ssh, and THEN set up the remote-desktop, from a 'local' connection you've already established.

@ cdmike : i do eventually want to be able to do truly remote work, but for now this works just fine. once i get more serious about it i think i'm going to set up NX, since it seems more secure and able to use ssh from start to finish. but i'm not familiar enough with ssh to open that can of worms just yet. thanks for your help!

---

### Post by ijason on 2008-12-05
ha.. and now TightVNC connects as well. that 'only allow local connections' check box had been stopping me all along!

---

