---
title: "Can't make password blank for network printer"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by bertros on 2005-07-27
I am a relative newbie looking for a little help.
I am trying to print from my Ubuntu box to a Canon Pixma mp750 printer connected to an XP box.   I have Samba up and running and am able to see shared folders.  I am using Turboprint on my Ubuntu box because it had the correct printer drivers easily accessible.

When I go to System>>printers>>properties>>connections, there is a five-character hidden password in the field (I don't use any five-character passwords).  There is no username in its field.  When I delete the password and close the "connections" tab and then re-open it, the hidden is password is back.  If I try to print then I get the "NT_access_denied" error.  Interestingly, if I delete the mystery password and then print a test page without closing the connection tab, then the test page prints.

Does anyone know how I can get rid of this password?  I have the shared printer set up to share to guests, and with previous networks set up like this it worked only if the password and usernames were blank (like this one seems to be working for the test page).  Is this password in a config file somewhere?  I have looked around with my very limitied linux knowledge and can't really find it.  Since it is five characters long, could it be "guest"?

I would really appreciate any help.

thanks.

---

