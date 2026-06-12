---
title: "Windows Network not seeing ubuntu hostname"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by Maggot on 2006-09-22
I'm having trouble with my windows network computers seeing my ubuntu linux box hostname.

I can ping any window hostname from ubuntu no problem but none of my window machines can ping the name of my linux box.

Strange thing is it worked before but I had to do a re-install of ubuntu and now it doesn't.

I researched this all day yesterday and tried several suggestions from here but none really seemed to match my problem.

I can connect/ping to the linux box using IP address from any window cpu.

My setup is as follows:

Windows NT Server 4 running DHCP. No DNS of any type.
Windows XP workstations
ubuntu linux box as a web server only.

All within an Internal LAN.

I'm trying to avoid giving the linux box a static IP and modifying all window computers hosts files.  

Any suggestions what the issue may be?

---

### Post by Iowan on 2006-09-22
**/etc/dhcp3/dhclient.conf** has an option to send the hostname.  There are more/better details in another thread around here somewhere.
[http://www.ubuntuforums.org/showthread.php?t=177832]("http://www.ubuntuforums.org/showthread.php?t=177832")
Here's one...

---

### Post by Maggot on 2006-09-22
> **Iowan said:**
> **/etc/dhcp3/dhclient.conf** has an option to send the hostname.  There are more/better details in another thread around here somewhere.
[http://www.ubuntuforums.org/showthread.php?t=177832]("http://www.ubuntuforums.org/showthread.php?t=177832")
Here's one...

Yeah, that was one I tried yesterday, no joy.

---

### Post by spd106 on 2006-09-22
Have you tried winbind? It worked great for me. Just make sure you put wins in the /etc/nsswitch.conf file. There are are a few threads around with more details.

---

### Post by Maggot on 2006-09-22
> **spd106 said:**
> Have you tried winbind? It worked great for me. Just make sure you put wins in the /etc/nsswitch.conf file. There are are a few threads around with more details.

Yes, read that thread too :D   Still didn't work.  Whats weird is it worked before without doing anything #-o

---

### Post by acefreely on 2006-09-22
You'll have to have some type of name resolution for the windows machines to ping the linux box by hostname.  If you don't have DNS or WINS on a machine, you'll have to use host files or lmhost files.

Windows machines can discover each other by broadcasting for netbios names.  If your machine is running samba and has a netbios table this may work.

Try (where IP is the IP of your Linux box)from a win box...

```
nbtstat -a 192.168.2.150
```

If you get something like this
```

           NetBIOS Remote Machine Name Table

       Name               Type         Status
    ---------------------------------------------
    LINUX          <00>  UNIQUE      Registered
    LINUX          <03>  UNIQUE      Registered
    LINUX          <20>  UNIQUE      Registered
    DOMAIN         <00>  GROUP       Registered
    DOMAIN         <1E>  GROUP       Registered

    MAC Address = 00-00-00-00-00-00
```

then you might be able to resolv the name via netbios broadcast...

---

### Post by spd106 on 2006-09-23
Do you have a firewall running on the linux box? eg firestarter. It could be blocking netbios name requests.

---

### Post by Maggot on 2006-09-24
> **spd106 said:**
> Do you have a firewall running on the linux box? eg firestarter. It could be blocking netbios name requests.

Hmmmm....firestarter is installed but as far as I know isn't started until I start it.  I'll remove it just to make sure that's not the problem.

acefreely, I'll try that today. Have to go into work for a few things.

---

### Post by Maggot on 2006-09-24
nbtstat and removing firestarter didn't work.

I think I'm gonna hafta bite the bullet and give it a static IP then modify workstation hosts file.  Only have 12 computers so it won't be that bad. :D

---

### Post by dix_ans on 2006-09-27
> **Maggot said:**
> Yeah, that was one I tried yesterday, no joy.

I had the same problem until I've noticed that the line in dhclient.conf should read something like:

```
send host-name foo;
```

Instead of 

```
send host-name foo.mshome.net;
```

Maybe it is evident for everybody that you should not include the dns-domain, anyway not for me. 

I hope this will help you!

---

### Post by h0ax on 2006-09-28
hi sir
read your post and it is the exact same as my problem
-- figured out a way to fix it tho -- at least I think..

If you don't have samba installed - install it
otherwise - edit /etc/samba/smb.conf
right above #### Networking #### - I added the line:
netbios name = your_hostname

seems to work
good luck:mrgreen:

---

### Post by tbonius on 2006-09-28
dhclient send-hostname is used for the DHCP server to dynamically register the hostname into DNS.  If you do not use DNS or WINS for name resolution, then you would be relying on NBT broadcasts in order to resolve the computer by its NetBIOS name (assuming that SMB is open and that there is no firewall blocking NBT requests.. etc..)

I recommend verifying that all machines user the same FQDN suffix and are all exisiting within the same NBT workgroup name.  If you are using a Domain (why the hell are you using NT4 again?) then I also recommend using a name service provider such as DNS or WINS.

Verify that the Linux machine can resolve its own name via /etc/hostname and/or /etc/hosts.  Verify the NBT name string matches its hostname and you should be golden.

The only other issue can occur with LMservice level announcements.  NBT has an application layer service that performs announcement on the network as to its OS and servie level.. that way it has authority to keep a "Browse List" of available NBT names on the network.  Disable Master and Local Browser services and OS levels for Samba.. it can sometimes fight with other Windows machines on the network.

T

---

