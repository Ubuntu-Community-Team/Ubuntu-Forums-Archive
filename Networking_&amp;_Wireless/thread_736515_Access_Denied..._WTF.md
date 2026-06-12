---
title: "Access Denied... WTF?"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by lenswipe on 2008-03-26
Hello there, i asked this in server platfoms but i didnt get a reply so im posting it here...


> > **lenswipe said:**
> Hi there

im trying to start a samba domain controller, before you say that the problem resides with samba, it doesnt...


I type the command ```
net rpc user <<username here>> add -U root
``` 
(i am already root before i type this so sudo ISNT missing :))

terminal returns to me with "NT_STATUS_ACCESS_DENIED_"

and something about error connecting to 127.0.0.1 

i am nearly finished setting up my domain, all i need to do is add domain users however i cant join a machine to the domain until i have a user with privaliges to do that on the domain itself, and i cant do that till i get around that problem..

please help

-lenswipe



---

### Post by Eiríkr on 2008-03-26
This does indeed sound like a problem with your Samba configuration, probably somewhere in the two lines:
```
interfaces = ....
bind interfaces only = yes
```

From [the smb.conf man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BINDINTERFACESONLY"):
> If bind interfaces only is set then unless the network address *127.0.0.1* is added to the interfaces parameter list [noparse]smbpasswd(8) and swat(8)[/noparse] may not work as expected due to the reasons covered below.

To change a users SMB password, the [FONT="Courier New"]smbpasswd[/FONT] by default connects to the *localhost - 127.0.0.1* address as an SMB client to issue the password change request. If bind interfaces only is set then unless the network address *127.0.0.1* is added to the interfaces parameter list then [FONT="Courier New"]smbpasswd[/FONT] will fail to connect in it's default mode. [FONT="Courier New"]smbpasswd[/FONT] can be forced to use the primary IP interface of the local host by using its [noparse]smbpasswd(8)[/noparse] *[FONT="Courier New"]-r remote machine[/FONT]* parameter, with *[FONT="Courier New"]remote machine[/FONT]* set to the IP name of the primary interface of the local host. 

So have a look at your conf file, it sure sounds like that's the issue.  

Cheers,

Eiríkr

---

