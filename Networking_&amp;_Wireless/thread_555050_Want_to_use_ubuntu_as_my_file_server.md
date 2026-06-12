---
title: "Want to use ubuntu as my file server"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by soultang on 2007-09-19
I had post this in beginner talk but it might be a bit advanced for there ... any weay I have a ubuntu box that i want to use as my file server ... and I have several Mac's as clients. how do i get to the files on the ubuntu box? ..  i understand samba a bit ... but i'm very confused.....  please help if you can.

thanks  soul

---

### Post by kidders on 2007-09-20
Hi there,

I wouldn't recommend using Samba, unless you have a good reason for wanting to do so. You see, Linux and OSX are very much closer to each other under the hood than Windows and OSX are, so it seems unnecessary to expose your clients to the limitations of Microsoft's networking protocols ... unless of course, you need/want to do so.

Theoretically, NFS is probably the most "natural" protocol to use, since both OSX and Linux natively support it. Using NFS with MacOS is not normally very practical though, so again, I would suggest not using it, with the exception of certain occasions where it works well. One example might be where all of your Macs' /Users directories were stored centrally ... a scenario NFS would probably fit very nicely.

For more general use, I would recommend using AFP and mDNS (aka Bonjour). That would give you a more user-friendly result, suitable for doing things like accessing your Linux box's home directories remotely, or sharing movies, etc. Your Apples require no configuration to use AFP. Your Linux server box would need netatalk and avahi (or any similar mDNS service) installed on them.

Two observations:[LIST=1]
[*]At first glance, AFP server configuration is a little intimidating. _Basic_ file sharing is, however, incredibly straightforward. I can go into more detail if you like the AFP option.
[*]It may seem weird to have to involve things like avahi in file sharing. In actuality, it's quite neat though. Apples use mDNS to advertise all sorts of services to each other, and is the thing that would make your shares pop up in Finder. You can also use it to integrate your Linux file server with iTunes, Safari, and so on.[/LIST]As you mentioned, a third option is Samba. The only advantage Samba has is that everybody naturally *has* to support Microsoft networks to some degree ... which makes it useful in multi-OS environments. It's irritating as hell though. As a simple example, using it on your network would create situations where something with a filename legal both in Linux & OSX could become unsharable, simply because Windows wouldn't like the look of it.

Anyhow, both Netatalk and Samba come with workable default configurations on Ubuntu, so getting started with either of those *should* be a matter of installing them. NFS is slightly different ... I would recommend reading "man exports" for details on that option.

---

### Post by dannemil on 2007-09-21
I set up an ubuntu box as my server on my home network using Samba. I used this howto and it worked fine.

[https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88]("https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88")

You'll see a section called Configuring your computer as a server. That helped me configure the ubuntu box as a server.

---

