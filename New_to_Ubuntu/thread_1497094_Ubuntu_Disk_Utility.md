---
title: "Ubuntu Disk Utility"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-30
I am trying to use the Ubuntu Disk Utility (System / Administration / Disk Utility) to monitor the disks on my server.

Set up is kind of easy.  So easy that I wonder if there was something that I did not do.  

What I did was go to File / Connect to Server

I then entered my server IP.  At the prompt I typed yes and logged in as root with the password.

Trouble is that I then get the following message (and google gives me zero search results .......)

buffer_get_ret: trying to get more bytes 4 than in buffer 0buffer_get_int: buffer error

---

### Post by roger_1960 on 2010-05-30
Hi

I suspect that the Ubuntu Disk Utility can only look at the machine on which it is installed.  You would need to sit at your server to use it there (assuming its installed on that machine).  Not sure about your login problem.

---

### Post by expatCM on 2010-05-30
It was good of you to reply but I not sure that I agree with you.  

The dialogue at the menu File does say Connect to Server and I do not think that would be necessary is the program was designed to run only on a local machine.  Indeed, if it were to run on a server only it would probably not be a gui and there would have to be some way of notifying the clients of a problem or you would need to be logged into the server to see any drive errors.

The other reason why I think it is for remote access is that the left column of the page is titled Storage Devices and there is a heading saying Local Storage.  Presumably when connected to a server then there is another category appearing?

---

### Post by roger_1960 on 2010-05-30
Hi again

The version I have, Palimpsest Disk Utility 2.28.0 , doesn't have that option under File, must have changed with Lucid.........

---

### Post by Bob Bertrands on 2010-05-30
You probably need to get a deamon running on your server first.

EDIT: 
My disk-utility software says the connection will be made using ssh.
I assume you have openssh-server installed on your server?

---

### Post by expatCM on 2010-05-30
Ah ...  yes, possibly since the latest stable is 2.30.1

Bob, you say "You probably need to get a deamon running on your server first."

Ok, that sounds really good but also fair to say I have not a clue what that means or rather what to do about it.  Any clue please?

---

### Post by Gone fishing on 2010-05-30
If you want to monitor your server why not try Munin. Munin allows you to monitor many things on your server as well as disk usage.

---

### Post by Bob Bertrands on 2010-05-30
This file:
[URL="http://git.gnome.org/browse/gnome-disk-utility/tree/?h=master"]```
[/URL][root]("http://git.gnome.org/browse/gnome-disk-utility/tree/?h=master")/[src]("http://git.gnome.org/browse/gnome-disk-utility/tree/src")/[gdu]("http://git.gnome.org/browse/gnome-disk-utility/tree/src/gdu")/[gdu-ssh-bridge.c]("http://git.gnome.org/browse/gnome-disk-utility/tree/src/gdu/gdu-ssh-bridge.c")
```
 
says the disk-utility will try to connect to an ssh server using this syntax:
```
ssh -R 0:localhost:LOCAL_PORT
```

```
/* Here's how it works
 *
 * - Client sets up a DBusServer on port LOCAL_PORT
 *   - we try a number of ports (in the 9000 to 10000 range) until this succeed
 * - Client creates a big random number SECRET
 * - Client creates a ssh connection to Server requesting a port-forward to Client:LOCAL_PORT
 *   - using -R 0:localhost:LOCAL_PORT
 * - Client parses REMOTE_PORT from "Allocated port <NUM> for remote forward to localhost:LOCAL_PORT"
 * - Client launches "udisks-tcp-bridge -p REMOTE" on Server and then writes SECRET and then a newline
 * - Server (effectively, ie. through the bridge) connects to Client:LOCAL_PORT
 * - Server invokes the org.freedesktop.UDisks.Client.Authorize with the SECRET string
 * - Client checks SECRET
 *   - if it doesn't check out, and error is returned and Server is disconnected
 *   - otherwise the method returns
 *
 *  Client can now use the D-Bus connection - Server is guaranteed to forward method calls and signals
 *  to and from the org.freedesktop.UDisks service running on Server
 *
 *  The reason we pass have an authorization SECRET is that otherwise
 *  malicious users on both the Client and Server may interfere.
 */
```

---

### Post by Bob Bertrands on 2010-05-30
can you check if you can execute this command on  your server?
```
udisks-tcp-bridge
```

if not, take a look at this page:
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/568926](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/568926)

---

### Post by expatCM on 2010-05-30
just looked at Munin.  Well I really do not know ....  the website has quite a few holes and the documentation is not great.  All I am trying to do is watch the hard drive health on the server.

Bob ....  well you certainly have your finger on the pulse.  I have to read your posts again,  carefully to understand everything you present.  I think I am not as awake as you are ...

Yes, I have ssh installed and running.  The command udisks-tcp-bridge on the server returns command not found.  It is a Debian server but I cannot see the difference from Ubuntu.  The launchpad article seems to present a solution but I first have to try and understand it in context so that I have at least half a clue of what I am doing.

---

### Post by Bob Bertrands on 2010-05-30
Good luck

Secret to staying awake:
If you had the same level of cafeïne in your blood as I have now you would be death

---

### Post by Gone fishing on 2010-05-31
I use Munin to check disk usage by users. 

For disk health Webmin has a module for checking Smart status etc 

I also use Raid1 and also have it set up so the sever emails me if it goes out of sync

---

### Post by expatCM on 2010-05-31
"I use Munin to check disk usage by users. " - now that I do not quite understand ....  but I miss many plots.  If (perhaps you don't) you have quotas enabled then disk usage should be reasonably under control?

"For disk health Webmin has a module for checking Smart status etc".  Well I do have Webmin installed and I did not know about this module.  Thank you for mentioning this.  I have a problem though, I just installed through webmin but it seems that webmin just installs the webmin module and not the program it controls.  I get the message that "SMART control command smartctl was not found" so I guess there is something cool to install that I have not quite yet discovered ...

---

### Post by expatCM on 2010-05-31
seems that you need to 

apt-get install smartmontools

---

### Post by expatCM on 2010-05-31
ok ... so this is a sort of interesting module.

I now have all the drives listed.  But I cannot see much purpose in the module.  I cannot see what it actually does.

But I may not have it properly set up yet.  I can see for each drive

Supports SMART? Yes
SMART enabled? 	No

I thought that SMART would have been on by default.  Does anyone know how to enable SMART on the drives?

---

### Post by Gone fishing on 2010-05-31
Do you have smart enabled in BIOS?

---

### Post by Gone fishing on 2010-05-31
I do have disk quotas but not for all users, some I allow to use as much space as they want, also the samba share folder i didn't use quotas on. I've found Munin generally quite handy to just keep an eye on things. A nice page of graphs easy to see if somethings going strange.

---

### Post by expatCM on 2010-06-01
Well you were right about the smart bios setting.  I looked at the output from dmidecode and it said nothing abut smart (to my disappointment) and so I rebooted the server and took a look at the bios settings.  Enabled smart and now have lots of information for each drive.

I think I am now disappointed with this Webmin module since even though it is called Smart Drive Status it does not actually do anything, it is only a report generator, it does not send out a warning if there is a problem, it just lists information.  Sorting through that is not fun and also means that you need to log on to your server to look at this module each day to see that the drives are healthy.

In turn I note 

Drive 1 - Raw Read Error Rate 	0 
Drive 2 - Raw Read Error Rate 	121372612 
Drive 3 - Raw Read Error Rate 	0 

Well ... I would have thought that drive 2 had a problem but apparently "SMART overall-health self-assessment test result: PASSED"

So whilst this module tells me all about the smart information, what I really need is to find a simple program that will monitor the drives from a client and then tell me explicitly if a drive is going to fail.

---

### Post by Gone fishing on 2010-06-01
OK have a look at 

[http://techgurulive.com/2009/04/08/how-to-set-up-smart-monitoring-in-ubuntu-smartmontools/](http://techgurulive.com/2009/04/08/how-to-set-up-smart-monitoring-in-ubuntu-smartmontools/)

Seems that the tool can send will send you an increasing frequency of emails as the drive slowly fails.

But why not run RAID1 or similar? and get the system to email you if it goes out of sync and then investigate and if needed replace the failing drive.

---

### Post by expatCM on 2010-06-01
That is a nice link .......  thank you for sharing.

Why not raid1 ...  well ...  hmmm ...  good question.  Basically when I set up the server it was one drive but that is now up to three.  To change over to a raid now would be quite a lot of pain so ..  until the next server setup I think it is separate drives ... 

I started this thread reporting that the Ubuntu Disk Utility is reporting the error "buffer_get_ret: trying to get more bytes 4 than in buffer 0buffer_get_int: buffer error " when connecting to a server from a client.  I think this may be a bug.  I have managed to get help from a person in the States who has done exactly the same thing as me and gets the same error notice.  Unlike me, he knows what he is doing ..........

---

### Post by Gone fishing on 2010-06-02
I think making Raid1 on an existing setup including / would probably be painful, but raid for /home, /var/lib/ might be quite easy - create the raid mount as /newraid copy the files over from /home then remount as /home. I guess that its /home that you can not afford to loose. You could then copy /etc etc onto the partition and if disaster struck it would be quite fast to recover.

[http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server)

---

### Post by expatCM on 2010-06-03
I was thinking to stop being lazy and use clonezilla .........  :)

The link to cmu.edu does not seem to work ...  well not in this part of the world.

---

