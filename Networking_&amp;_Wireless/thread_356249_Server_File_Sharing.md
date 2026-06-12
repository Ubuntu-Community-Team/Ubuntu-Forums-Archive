---
title: "Server File Sharing"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Rich78 on 2007-02-08
Hi,

I'm wanting to setup a business network which will completely run Ubuntu for both clients and the main server.

I want the server to host and manage the users and groups and also to serve as a file server, so share directories that will be accessible to various clients but have user restrictions so that only certain clients can access certain directories (determined by their user or group ids).

Could you possibly tell me which the best way to go about implimenting this?  Which technologies should I use?

Thanks

---

### Post by lkagan on 2007-02-08
The traditional ways to go about doing this are to use NIS for central user management and NFS for file sharing.  There are, however, other options.

Larry Kagan

---

### Post by Rich78 on 2007-02-08
Thanks,

I had been going down that route, but with the lack of info about it on the Ubuntu forum I thought perhaps I was going down the wrong route.

Is Samba one of the other options and if so how does it compare?  I haven't gone near that as I thought it to be more of a Windows integration system rather than a *nix to *nix method.

With regard to NIS, do I just setup Users on the main server and the clients will get their profile from NIS, the same as with Windows Server?

---

### Post by lkagan on 2007-02-08
Samba is definitely another option.  If you ever want windows users to gain access to your file structure, this is the route you'll need to go.  However, the two are not mutually exclusive; meaning you can do both.  Samba will act as the windows users version of both NIS & NFS.  So start with NIS and then add on Samba in the future if you so desire. 

Fore more specific questions about configuration and such, I'll refer you to the NIS howto at [http://www.tldp.org/HOWTO/NIS-HOWTO/](http://www.tldp.org/HOWTO/NIS-HOWTO/)

Larry Kagan

---

