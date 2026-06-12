---
title: "Hosts file and networking"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by madsurfer on 2008-04-27
Hi
Have just upgraded to Hardy Heron and trying to compile something but am getting the following error:

ping: unknown host geko80

When I am on geko80! Have checked my host file of which I include a copy here
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts
192.168.1.80 geko80

localhost ip6-localhost ip6-loopback

Does any one know what I have  done wrong?
Thank you
Adrian

---

### Post by jetsam on 2008-04-27
Go to system-->administration-->network, and make sure your hostname is set in the 'general' tab.

If that looks ok but isn't working for some reason, you can add your hostname manually.  Just add this line:
```
127.0.1.1     gecko80
```
Underneath the '127.0.0.1    localhost' line of your hosts file with a text editor.

You may need to restart networking after doing this:
```
sudo /etc/init.d/networking restart
```

**Added**:  Just saw the '192.168.1.80 geko80' line.  I'd take this out.  It's better to use the 127.0.1.1 form above for what you're doing because it will never need to change and will work even if the network is down.  

Still, I think what you had should have resolved, so you may have a different problem.  If the above changes don't work, check your /etc/nsswitch.conf file, and make sure that 'files' is first on the list after 'hosts:' on the 'hosts:' line.

---

### Post by madsurfer on 2008-04-28
Well have seen some further problems, the main thing is not being able to use sudo so can not switch to root!, Kind of stops you from doing anything! have checked the network setings pop up and the general tab is OK but don't know what further to do?

Has anyone got any other ideas?

Adrian

---

### Post by Monicker on 2008-04-28
> **madsurfer said:**
> Well have seen some further problems, the main thing is not being able to use sudo so can not switch to root!, Kind of stops you from doing anything! have checked the network setings pop up and the general tab is OK but don't know what further to do?

Has anyone got any other ideas?

Adrian

Use the recovery mode option in the boot menu to get to a root shell.  Then modify /etc/hosts as suggested.

---

### Post by madsurfer on 2008-04-28
I can't login as root anymore, sudo gives a message

sudo: unable to resolve host geko80

:confused:

This is the same error that I had before! has anyone got any ideas of how to move forward with out reinstalling!

Adrian

---

### Post by Swiftfeet8 on 2008-04-28
That error means that you aren't able to resolve gekco80, it doesn't mean that you can't do "sudo".  If you were unable to do "sudo" you would get a different error saying that you don't have permissions or something like that.

Have you tried just pinging as a regular user, not through "sudo"?

Type "hostname" in a terminal and make sure that you are in fact gecko80.  Also verify that you can ping 127.0.0.1 (no reason you shouldn't be able to).

---

### Post by jetsam on 2008-04-28
A few people seem to be having similar problems.  

Interesting, a user in this thread reports gksudo working fine:
[http://ubuntuforums.org/showthread.php?t=772617&highlight=can%27t+sudo]("http://ubuntuforums.org/showthread.php?t=772617&highlight=can%27t+sudo")

If that's true, it should work to open a terminal and try:
```
gksudo gedit /etc/hosts
```
and then make the changes to your hosts file.  

There's a longer thread developing about this issue here:
[http://ubuntuforums.org/showthread.php?t=615579&highlight=can%27t+sudo]("http://ubuntuforums.org/showthread.php?t=615579&highlight=can%27t+sudo")

---

### Post by Monicker on 2008-04-28
> **madsurfer said:**
> I can't login as root anymore, sudo gives a message

sudo: unable to resolve host geko80

:confused:

This is the same error that I had before! has anyone got any ideas of how to move forward with out reinstalling!

Adrian

Recovery mode from the console does not work for you?  You can also try the gksu method.  The former approach worked for me.

---

### Post by ShaunBrown on 2008-04-28
I had the same problem recently. I had to use ctrl+alt+F1 to go into TTY mode. Then login as root. Next use the killall command.
$ killall gdm
This stops Xserve
Next use startx to start a root xwin instance
Next edit your hosts file with gedit
Fix what you need to in the hosts file
Then restart

---

### Post by madsurfer on 2008-05-05
have still got a problem every time try to do this, gksudo gedit /etc/hosts.  the cmd just sits there and does nothing!!  adrianr@geko80:~$ 

gksudo gedit /etc/hosts

Adrian

---

### Post by jetsam on 2008-05-05
It didn't make much sense to me that gksudo would work.  I suggested it because it seemed to work for a few other people on the forums.  Try Monicker's suggestion--  reboot, and from the grub menu choose recovery mode.  This should give you a root prompt and allow you to do
```
nano /etc/hosts
```
and fix the hosts file from the terminal.  

If that doesn't work, there's ShaunBrown's method, or failing all else, booting from a live cd and fixing the file from there.

---

### Post by madsurfer on 2008-05-05
Hello
now unable to run this cmd!! the terminal just sits there not doing noyhing!! what am I doing wrong?

futher if I use vi I get the following 
 sudo vi /etc/hosts

sudo: unable to resolve host geko80

---

### Post by jetsam on 2008-05-05
What happens when you reboot in recovery mode?

For me, I get a text only sequence of boot messages and then a root prompt:
> root@myhost:~#

You shouldn't need sudo from this point.  You're root already.

---

### Post by Iowan on 2008-05-05
Anything [here]("http://ubuntuforums.org/showthread.php?t=615579") help - especially the link to bug?

---

### Post by jetsam on 2008-05-05
I'm guessing a bit, but I'm thinking madsurfer is just not getting into recovery mode.  

When your computer starts up, there should be a short period when it says "grub loading stage 1.5."  You need to press escape at this point to bring up the grub boot menu. You only have a few seconds by default.   

This should give you a boot options menu with options to boot into the standard kernel, the kernel in recovery mode, and memtest86+.  You want the (recovery mode) option.

Sorry; I've changed my default settings, and I forgot how hidden this usually is.

---

