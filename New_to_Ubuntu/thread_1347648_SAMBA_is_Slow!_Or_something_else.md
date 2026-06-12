---
title: "SAMBA is Slow! Or something else?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by whackstar on 2009-12-06
Hi People, Sorry this is the first time post. I am also a novice to Ubuntu.

I have a home network that has a Ubuntu Server that acts a media server using Twonky Media I also have Samba running as a basic file server. I have just upgraged my network using belkin 1000mbs network hubs. But I am still getting V slow network transferes. I think problem is Samba. I just need a sounding board to try and solve this problem It takes about 20mins to transfere 1gb of data.

My client machines are 1 xbox, 1 mac pro and several windows laptops.

The card in server and mac are 1000mbs cards and are both connected to the LAN via belkin 1000mbs homeplugs. The homeplugs show they are connected at 200mbs + speeds and the cards are connecting at 1000mbs.

I have also enclosed my smb.conf file in the hope that I've missed somthing. But I have treid the socket alterations in the hope that it might improve performance. No luck!

Thanks to anyone who might be able to help.

Best wishes,

Whackstar

[global]
        log file = /var/log/samba/log.%m
        guest account = wayne
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        write list = @admin
        guest ok = yes
        map to guest = bad user
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        disable netbios = yes
        netbios name = Samba
        writeable = yes
        server string = %h server (Samba, Ubuntu)
        invalid users = root
        default = global
        path = /media/disk
        unix password sync = yes
        workgroup = hackmanlan
        security = share
        syslog = 1
        usershare allow guests = yes
        panic action = /usr/share/samba/panic-action %d
        encrypt passwords = yes
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

I have done some tweaking and managed to go from 1.5mbs to 3-5mbs. But both twonkey & samba transfer at similar speeds. Could it be a hardware fault? Could there also be a service that is running that could be holding back the lan speed?

I'm tierd and shooting in the dark now!

---

### Post by Cheesemill on 2009-12-06
Do you know what speed your transfers a going in Mb/s?
 
I'd expect real-world speeds of about 5-10Mb/s from a setup like that.

---

### Post by whackstar on 2009-12-06
Thanks for your reply. Its looking like 1.5mbs. That's using twonky via a web browser. Like I say I'm a novice to all this. But surly its possible to transfer quicker then this over a local network?

Thanks again.

---

### Post by Cheesemill on 2009-12-06
That could be about right. I've just done a quick calculation (on the back of an envelope mind you so don't quote me on this).

We'll start with the 200Mb/s your plugs are reporting:

200Mb/s * 0.7 = 140Mb/s (powerline networking protocol overhead)
140Mb/s * 0.7 =  98Mb/s (TCP/IP networking overhead)
98Mb/s * 0.125 = 12MB/s total network data throughput.

If your traffic is going through the powerline to a switch and back through the powerline then divide this by 2 (as you have 2 lots of transmitting/receiving going on).

This gives about 6MB/s theoretical maximum data transfer between the two machines, and that's not yet taking into account that Samba isn't a very efficient protocol either. Also this assumes your house wiring is in perfect condition with no interference. Add to this the fact that badly tuned network drivers can cause up to another 90% decrease and you'll see that 1.5MB/s is probably acceptable.

---

### Post by whackstar on 2009-12-07
Oh! Well at least I am not going crazy. I must admit I am a little depressed tho! Was hoping to transfer things a little faster. My i tunes library takes for ever to load! Can you suggest any ways in which I can speed things up or do I have to suck it up?

I guess this is where i show my novice side I always assumed that with a 100mbs network data flowed at 100mbs! Now you have explained it it makes more sense. Thank you for the comments.

---

### Post by Cheesemill on 2009-12-07
You can speed things up by going straight from your gigabit switch through cat 5e/6 cables to your devices. You will see speeds of up to around 70MB/s if you do this (assuming your hard drives can manage this throughput). :)

PS - Most people don't realise the difference between Mb/s and MB/s.

8 Mb/s = 1 MB/s (8 bits = 1 Byte)

---

### Post by whackstar on 2009-12-09
So as the server and the mac are connected directly to the network via network plugs. Neither of them go through the router. That is a standard BT router which is also connected to the power line via another net gear plug. Would the router still slow everything down? Even tho the server and mac are not directly wired into it? I just assumed that as the Server and the Mac are connected directly to the power line it would run at  the faster speeds? I might try the direct plug method.

---

### Post by renkinjutsu on 2009-12-09
If you need to transfer lots of stuff from your mac to your server, use the NFS protocol instead of SAMBA... it's MUCH faster in my opinion and more intuitive.

---

### Post by doas777 on 2009-12-09
> **Cheesemill said:**
> You can speed things up by going straight from your gigabit switch through cat 5e/6 cables to your devices. You will see speeds of up to around 70MB/s if you do this (assuming your hard drives can manage this throughput). :)

PS - Most people don't realise the difference between Mb/s and MB/s.

8 Mb/s = 1 MB/s (8 bits = 1 Byte)

Interesting. my network is gigabit througout, and I only get between 35-40MB/s at least with samba. that does not seem to be a limit on bandwidth however, as I can get more than one connection going (though not 2@35MB/s)

---

### Post by wiz-oz on 2009-12-18
I have suffered this issue too, and read various suggestions on how to tweak samba. Nothing seemed to work, until I stumbled upon this:

[http://www.linuxquestions.org]("http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/").

In this thread someone suggested samba was slow because the realtek drivers that get installed from the repositories are buggy.

My nas box is build with a point of view atom330 with an onboard reaktek 8111, and that used the R8196 driver that was installed.

I have downloaded the sources from realtek and compiled them. After the build and installation I blacklisted the R8196 and rebooted the box. Since then Samba performs equal to nfs, so all windows users here (wife & kids) are all happy now.

The other thing I was eventually going to do is install the nfs services from microsoft and have them use nfs to access their shares, but needless to say this fix was easier.

So if you suffer slow performance with samba, and you have a realtek chip, try to change the driver and see if that helps.

Cheers,

Wiz

---

### Post by BMWolf on 2010-04-16
> **wiz-oz said:**
> ... reaktek 8111, and that used the R8196 driver that was installed.

My board uses the 8111 too and using the latest driver increased the speed by a factor of 2, but my reads are still 3-5x slower than my writes. Writes are 20-50MB/sec and reads are 6-12MB/sec. I'd like my reads to at least match my writes. I'm baffled.

What kind of throughput are you getting?

link to a thread I started: [http://ubuntuforums.org/showthread.php?t=1455768](http://ubuntuforums.org/showthread.php?t=1455768)

**Edit:** Speed is magically performing as I would expect! I did a few tweaks to the Samba config, restarted Samba, and didn't see any change whatsoever. Came back 24 hours later and it all works as expected, WTH! Maybe Vista was indexing the drive or something.

---

