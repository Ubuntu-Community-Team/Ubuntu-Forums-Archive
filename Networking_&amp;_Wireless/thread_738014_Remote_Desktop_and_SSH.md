---
title: "Remote Desktop and SSH"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by kpsmith on 2008-03-28
Right I've installed and configured ssh on my linux box and also configured vnc on the linux box, I'm trying to access it remotely from a windows machine.

Using putty i can connect to it using ssh with no problem, using VNC I can also connect with no problem so I know that both parts work.

What I want to do is connect to it using VNC but through the ssh tunnel, but i don't know how to make this work

I can login through putty using ssh but when I put in command

vncviewer kpslinux:0 or vncviewer localhost:0 it says it can't open display ""

How can I configure my linux machine so that whenever a vnc request is made it creates a ssh tunnel back to the machine requesting the vnc session and then connects? I also want to set it up so it will only initiate vnc connections over ssh.

I guess I will need to re-configure vnc to use the same port or configure ssh to redirect all vnc traffic over the ssh port?

Can anyone shed any light on this.

---

### Post by kevdog on 2008-03-28
What parameters are you passing through putty?  You need to enable port and X forwarding.

---

### Post by kpsmith on 2008-03-28
ahh i see ok hadn't though of that, I was just connecting with the hosname and port for the ssh i didn't set it up for forwarding ports or x. 

I guess i'll need to tell it to forward the vnc ports to the ssh tunnel ports? shouldn't be to difficult I guess

What will i need to tell it for the X forwarding?

I'm a bit new to ssh and putty i've used them both before individually for accessing different machines for different reasons but not to do anything like this.

---

### Post by kevdog on 2008-03-28
The server also has to be configured (in the sshd_config file) to allow X forwarding.  I dont think this feature is activated as a default.

---

### Post by kpsmith on 2008-03-28
Ok I'll look into that then, is it a line I will need to add manually or will it be there but set to no at the moment?

---

### Post by stefangr1 on 2008-03-28
I do this the same way as you want it to do.

(1) open putty, type in the ip-address you want to connect to
(2) go to the ssh tab, press tunnels, choose your source port (say 9509), fill in the destination, which is your internal ip address followed by the port that vnc server uses (in my case 10.0.0.1:5900)
(3) open vnc viewer, type in: localhost::9509

Good luck with it!

---

### Post by kpsmith on 2008-03-28
thanks for that, all seemed to work ok

I added the source port as the ssh port then followed as per your instructions, putty connects fine but I still get the same cannot open display ""

I'll check the ssh server settings and make sure X forwarding is enabled.

it will work!

---

### Post by stefangr1 on 2008-03-28
What do you type in to connect with vnc without ssh?

I don't think this has anything to do with x forwarding, since (but I'm not 100% sure) thats for forwarding x to an x server on a remote machine, so that graphical programs that run on the server can be used on the host. I think the problem here lies in what you type in in the vnc client to connect.

---

### Post by kpsmith on 2008-03-28
If I connect just using VNC then I put my remote WAN IP in the VNC client on the windows machine it connects to the standard linnux vnc port. I put in my password for the VNC service and it connects without a problem.

in putty I put in my remote WAN IP in the box and tell it to connect to the port I've chosen for SSH and it connects when configured as per your instructions it still connects fine but when I type

vncviewer localhost:0 i get the can't open display"" message even if I use the internal IP of the remote machine i'm ssh'd into it still does the same thing.

---

### Post by kpsmith on 2008-03-28
I just realised what I've done wrong I tried step 3 exactly as you put it i forgot to put the port in! I'll try that and copme back with feedback.

---

### Post by kpsmith on 2008-03-28
Nope still not working 

At the first putty screen I put in

REMOTE WAN IP and the SSH port a

In the tunnels section I specify the source port as the SSH port a then in the section below the internal IP x.x.x.x:5900 and click add

then once connected  I typed

vncviewer internalip::sshport

i also tried vncviewer internalip:0:sshport

Both brought up the same message

I've attached a screenshot to show what I typed, I've not displayed my remoe WAN IP as that would be inviting hackers to my doorstep.

---

### Post by stefangr1 on 2008-03-28
Oh...  now it's becoming very clear :)

You have to download a vnc client to run on the windows client machine.

You could use tightvncviewer:

[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)   ->  choose the Viewer executable

After you logged in with putty as described you leave the session open without doing anything with it.
Then separately open the vnc viewer executable, log in using localhost::9509, then your vnc password is asked and hopefully everything works as it is suppozed to.

---

### Post by kpsmith on 2008-03-28
I've got one of those already, so what I should be doing is in putty connecting via ssh to the remote linux machine in question with the relevant port forwarding setup in the tunnels part

then using the vnc client on the local windows machine connect to the remote linux box wan IP but using the ssh port instead of the usual 5900

makes sense now, is there no way to set up the linux machine so that when I connect to it through vnc it automatically creates ssh tunnel with the correct parameters first then initiates the vnc session?

---

### Post by stefangr1 on 2008-03-28
Yep! I hope for you that everything will work now.

I believe it is also possible to configure vnc4 in a way that it encrypts all network traffic automatically with ssh, but I have no experience with that.

---

### Post by kpsmith on 2008-03-28
Yupp that works, tunnel in with putty using ssh then initiate a VNC session using vnc to 

hostname:0:sshport

using hostname::sshport didn't work vnc threw up some error about it being the wrong server type.

now I just need to figure out how to make vnc4 initiate the ssh first.

---

