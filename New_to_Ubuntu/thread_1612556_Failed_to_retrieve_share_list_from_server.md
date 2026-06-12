---
title: "Failed to retrieve share list from server"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by keats4 on 2010-11-03
Hello all

Okay I do this:

-- Places
-- Network
-- Windows Network
-- WORKGROUP ( this is my work group name)

When I double click on workgroup I get this error:

"Failed to retrieve share list from server."

What could be the problem . . . thanks for any help in advance.

Just an idea: Does my "windows 2003" server need to support this "smb" protocol? Is this manually installed at the server side?

Can someone explain to a windows person what smb is. . .its the first time I'm encountering this.

Keat

---

### Post by janpol on 2010-11-03
What smb is?

[http://en.wikipedia.org/wiki/Server_Message_Block]("http://en.wikipedia.org/wiki/Server_Message_Block")

Maybe you don't have the smbclient package installed (I don't know if you need any extra packages besides that one in order to browse shares).

```
sudo apt-get install smbclient
```

Or, if you are going to share folders from your linux box to windows clients, you could just install samba:

```
sudo apt-get install samba
```

Hope it helps

---

### Post by keats4 on 2010-11-03
It appears I already have the smbclient installed. Could someone please address the "share list error message"

Thanks so far
Keat

---

### Post by janpol on 2010-11-03
I've found this :D:

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

Also, there are a few threads talking about this issue:

Read coment #111:

[http://ubuntuforums.org/showthread.php?t=1082148&page=12]("http://ubuntuforums.org/showthread.php?t=1082148&page=12")

Read comments #9 and #10

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1357070]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1357070")

---

### Post by migs73 on 2010-11-03
> **janpol said:**
> I've found this :D:

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

Also, there are a few threads talking about this issue:

Read coment #111:

[http://ubuntuforums.org/showthread.php?t=1082148&page=12]("http://ubuntuforums.org/showthread.php?t=1082148&page=12")

Read comments #9 and #10

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1357070]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1357070")

Thanks for the link that tells how to use computer names on windows machines, that has been annoying me for weeks! Had to use IP addresses on a machine connected via a DHCP so IP changed every time it logged off/on. Now it'll connect without having to change anything. :)

---

### Post by phantomn on 2010-12-30
This is also a problem for me, when I followed the instructions the network joined perfectly and it all worked well. 
BUT my internet browsing speed was reduced. It was taking twice as long to load simple sites like google. 
When I switched it back however it returned to normal!

All I did was edit the smb config file, and the nsswitch config file. 

Any Ideas?

Cheers 
P

---

### Post by travlemon on 2011-02-21
> **phantomn said:**
> This is also a problem for me, when I followed the instructions the network joined perfectly and it all worked well. 
BUT my internet browsing speed was reduced. It was taking twice as long to load simple sites like google. 
When I switched it back however it returned to normal!

All I did was edit the smb config file, and the nsswitch config file. 

Any Ideas?

Cheers 
P

I'm still quite new to Linux and Ubuntu myself, so this may not be too helpful.  But, make sure your name resolve order in **smb.conf** looks like this:

```
   name resolve order = lmhosts wins bcast host
```

Also, 

make sure your **nsswitch.conf** hosts line looks like this:

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```


The order for those lines is important.  I've expeimented before, putting wins at the beginning of the name resolve order, and it killed Samba browsing for all of my Ubuntu machines.

I know that's not the issue you are having, but just an example of how it can be important to make sure you followed the instructions exactly.  Hope this helps.

---

### Post by picbits on 2011-10-16
> **travlemon said:**
> I'm still quite new to Linux and Ubuntu myself, so this may not be too helpful.  But, make sure your name resolve order in **smb.conf** looks like this:

```
   name resolve order = lmhosts wins bcast host
```

Also, 

make sure your **nsswitch.conf** hosts line looks like this:

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```


The order for those lines is important.  I've expeimented before, putting wins at the beginning of the name resolve order, and it killed Samba browsing for all of my Ubuntu machines.

I know that's not the issue you are having, but just an example of how it can be important to make sure you followed the instructions exactly.  Hope this helps.

I can confirm that this solves every problem I've had with this on the 4 machines with fresh installs.

---

### Post by hallon on 2012-02-13
> **travlemon said:**
> I'm still quite new to Linux and Ubuntu myself, so this may not be too helpful.  But, make sure your name resolve order in **smb.conf** looks like this:

```
   name resolve order = lmhosts wins bcast host
```

Also, 

make sure your **nsswitch.conf** hosts line looks like this:

```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```


The order for those lines is important.  I've expeimented before, putting wins at the beginning of the name resolve order, and it killed Samba browsing for all of my Ubuntu machines.

I know that's not the issue you are having, but just an example of how it can be important to make sure you followed the instructions exactly.  Hope this helps.

Ahh perfect solution for my problem with this as well! Thank you, how lucky am I to stumble upon this thread! :KS

---

### Post by woodbrick on 2012-06-14
> **hallon said:**
> Ahh perfect solution for my problem with this as well! Thank you, how lucky am I to stumble upon this thread! :KS

Same here. Samba was crashing my network connection on ubuntu 12.04

Changing the smb.conf file as above did it
Thanks

---

