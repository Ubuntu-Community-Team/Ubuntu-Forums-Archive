---
title: "Upload Connection for decent x11vnc connections"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2007-08-28
Hi there, 
according to Time Warner Cable I have a 5mbit download and a 3mbit Upload but that's bull!!! WHen I ran a test, my upload was around 60 kilobyte's/second. i use tightvncviewer as my vnc client. it's pretty tolerable as I said. I have done mythbackend-settings before, I have done apps like tovid-gui, gedit, firefox and yes it is slower than normal but like I said, I can actually get something done while bored at work. It's most likely because of your client isn't compressing the connection like tightvncviewer does. I use all defaults accept when it comes to the window, i tell it to scale it to 7/8 so that it doesn't take up my entire screen since I am at work. i'll look into another router maybe cause I know there's really no other settings I can change that would affect anything in my netgear router besides maybe the MTU but I thought it should 1500 shouldn't it? again, I can't right now check what my router is set at because my connection is down but I'll check it and let ya know so I can compare it to your MTU. lata.

---

### Post by newlinux on 2007-08-28
I'll set up tight vnc and try that out, right after I figure out how to better secure my ssh connection.

---

### Post by dannyboy79 on 2007-08-28
well first you can try other ports beside 22. also, you can use public/private key pair instead of pam authentification. They are rsa or dsa keys. You'll want to turn the id_rsa.pub key (this is the public key) into your authorized_keys file and then take the id_rsa with your on a usb key, this is the private key! then you can use puttygen to convert the id_rsa key into a key putty can use. then you point putty to the key located on your usb stick and it does a handshake with the key located on the server (~/.ssh/authorized_keys    NOTE: the actual filename is irrelevent, it just has to be specified what the name and where the key is located within your /etc/ssh/sshd_config) and then you would connect. you can also restrict it to users also. I only allow my user on, you can find out the option by typing man sshd_config. I think it's

AllowUsers yournamehere

also, I assigned a passphrase to my keys so even if I lost my usb stick and some1 was smart enough to know what the key.ppk file was for they would still be prompted for the passphrase to log into my server and they wouldn't know it and it would take more the 88 years to crack with todays dictionary attacks! that's about, then your ssh is pretty secure!


[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

I don't use ssh-agent though as I don't mind having to enter my passphrase all the time. Also, I put the authorized_keys file on all my other machines in the house as well as left the private key on my main ssh server within the ~/.ssh/ folder so that I could jump from 1 machine to the next within my network. I am guessing that's the true goal of ssh-agent but I never bothered to set it up.


[http://www.schwer.us/journal/2004/02/18/locking-down-an-ssh-server/](http://www.schwer.us/journal/2004/02/18/locking-down-an-ssh-server/)

the immediately above guide is suggesting to not enter a passphrase with the key pair but I don't agree with that becuase I keep mine on my usb stick and if I lose it some1 could then connect to my machine assuming they knew my external ip address.

denyhosts will add a ip address or FQDN to the hosts.deny if they fail 3 times to login. if you know any of the ip's or FQDN right away that you will be login in from then add them to the hosts.allow file that way if you mistype 3 times in a row, you won't be added to the hosts.deny file. 

[http://ubuntuforums.org/showthread.php?t=450853&highlight=denyhosts](http://ubuntuforums.org/showthread.php?t=450853&highlight=denyhosts)


Also, here's a site talking about an iptables rule that willl add dictionary attackers and block them based on connection attempts.
[http://lists.sans.org/pipermail/intrusions/2006-March/009130.html](http://lists.sans.org/pipermail/intrusions/2006-March/009130.html)

---

### Post by newlinux on 2007-09-11
Due to some ISP and work firewall issues I can't put ssh on another port, but I did end up installing and properly configuring denyhosts, and setting up tightvnc. VNC works okay, still a little slow, but usable. Maybe I'll play around more with teh compression settings. But I have a really slow upload connection at home, so there is probably only so much I can do. I also took some time to better secure some of the other services while I'm at it.

Thanks for your help (I'm typing this through tightvnc at work right now).

---

### Post by dannyboy79 on 2007-09-12
sweet, glad you got it working. one thing I need to figure out is how to get it so that if I need to restart my computer remotely, I can login thru ssh somehow and start a session. Currently what happens is:
for whatevers reasons I am messing around with something over ssh and or x11vnc. Then I need to restart my machine, so I either issue 
sudo shutdown -r now 
from the ssh session or I hit the Shutdown icon thru tightvnc. So the machine goes down and due to the -r switch with shutdown command, it restarts. So bascially at home my computer is sitting at the gdm Login Screen. 
I can ssh back into my box but can't use gdm to log me into a session so what do I do now? I was able to find info for enabling auto-login thru ssh by editing my gdm.conf file ( i think that's the file I changed) so that when I do a restart, my session is auto started  but I would prefer to not have auto login.
Any suggestions?
Yeah, I forget what my upload is but my tightvnc session definitely isn't fast, it's very slow and barely tolerable but it will allow you to do something when you really need a gui instead of ssh.

---

### Post by krunge on 2007-09-12
> So bascially at home my computer is sitting at the gdm Login Screen.
I can ssh back into my box but can't use gdm to log me into a session so what do I do now? I was able to find info for enabling auto-login thru ssh by editing my gdm.conf file ( i think that's the file I changed) so that when I do a restart, my session is auto started but I would prefer to not have auto login.


You will need root permission to connect x11vnc to an X server showing the GDM Login screen.   Basically because you need to pass "-auth /var/gdm/:0.Xauth" to x11vnc and that file is only readable by root.

More details here:  [http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager") Be sure to note the KillInitClients=false issue that GDM has described there.  

Also, in x11vnc version 0.9.3 dev tarball there are some new options "-find -env FD_XDM=1"  to have x11vnc try to attach to the Login display automatically (still needs to be run by root/sudo for the reason above).

---

