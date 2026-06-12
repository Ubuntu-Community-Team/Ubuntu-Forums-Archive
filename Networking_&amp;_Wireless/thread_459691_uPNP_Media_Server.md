---
title: "uPNP Media Server"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by aminchar on 2007-05-30
How can I setup ubuntu to be a network Media Server on intranet just like Windows Media Player Network Sharing Service allows using uPNP to share pictures, audio and video?

---

### Post by cantormath on 2007-05-30
> **aminchar said:**
> How can I setup ubuntu to be a network Media Server on intranet just like Windows Media Player Network Sharing Service allows using uPNP to share pictures, audio and video?

How do you want to access the files once the server is setup.  

You can easily setup a SSH server,   Just install openssh-server.  It should add itself to the /etc/init.d folder and start the ssh server on boot.  Then, you can ssh into the box with a ssh client and download whatever you want.  Note, the ssh client is built into Ubuntu, (Places>Connect to server or ssh from terminal) so there is no need for another client.  You can also use a samba server, which I think you can setup using the System>administration>File Sharing Settings.  It should install the samba stuff you need and you will need to set a samba password.  You can then see the ubuntu samba share folders on your windows network, meaning from a windows machine.  Lastly, I would say a FTP server might be to your liking, similar in usage to ssh but not as secure.

If you are looking for something like a streaming media server, that is a bit more intense, but you can do it using something like ICEcast, which is in the repositories,   There is also Camserv, and a bunch more.  

I recommend you look some howtos for whatever you choose just so you dont miss anything.  Everything is pretty dueable though, nothing to intense.

Hope that helps...

---

### Post by airflow on 2007-07-16
I have tried a couple of media-servers, and found [mediatomb]("http://mediatomb.cc/") to be the best. Your mileage may vary. It's not in the ubuntu-repositories yet, but you can easily add the apt-repo from the homepage.

Regards,
airflow

---

### Post by r76 on 2007-07-19
Just looking for the same thing myself.  I think.  Hell, I'm not even sure what I'm trying to do any more :p
I think what I really want is to add metadata for videos and keep them in a dynamically updating store so I can see what I've got - and browse by content tags and searching extended metadata (e.g. from TV listings).

But have a look [here]("http://www.jonobacon.org/?p=984"), there is an interesting discussion and I've found loads of things to try out.  A write-up of mediatomb is[ here]("http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me"), I'm going to try that one first.

---

### Post by njparton on 2008-01-17
I've just setup mt-daap foolishly thinking windows media player would be able to use it for receiving music over my home lan.

I now realise I need a upnp not daap server (aargh - took me 3 evenings to get mt-daap working!!).

Will Windows Media Player running under Vista be able to interface with Mediatomb?

Thanks

---

