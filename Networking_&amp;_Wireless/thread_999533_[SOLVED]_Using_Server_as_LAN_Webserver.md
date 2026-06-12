---
title: "[SOLVED] Using Server as LAN Webserver?"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by baruch60610 on 2008-12-02
I recently installed Ubuntu Server Edition (8.04) on an old computer that I want to use as a server on my LAN.

Among other things, I installed Apache, and set up a Website for local (non-Internet) use.  I got it all working yesterday, could see my Website from another computer on the LAN, and everything worked well (after some Forum members helped me with ssh and scp).

Today, I can't access the Website.  I can log in to the server through ssh and muck about as usual.  I can use the 'fish' protocol with Konqueror to manipulate files and do other tasks on the server.  I can ping the server and get a response.  I can even traceroute to it.   I just can't get it to show my Website.  I get a "403 Forbidden" error.  Rubbish, I say...

When I check the Apache error log, I'm told, "Symbolic link not allowed or link target not accessible: /var/www/baruch".  It is true that I use symbolic links to point to directories in my home directory, instead of putting them directly under /var/www.  So the problem looks like it's with the symbolic links.  However, I use the exact same configuration (with identical files) on my live, Internet Websites, and it has never given me any problems.  Besides that, the thing was working just fine yesterday.

I have checked the links and found them to be functional (I could access the directories through them).

I've checked that the ports are open for http.  I've even tried restarting Apache, in case it had some indigestion.  Still nothing is working.

I don't know what else to try.  I would appreciate any suggestions or links to any information that could help me get this straightened out.  Thanks

---

### Post by dollylamb on 2008-12-02
could you post in here your apache2.conf & httpd.conf? i want to take a look at them. Btw, how do you access your website? using dns or directly access through server name?

---

### Post by baruch60610 on 2008-12-02
Hi, Dollylamb:

Thanks for your response.  I've renamed all these files from the .conf extension to .txt, since .conf wasn't one of the accepted extensions for files.

Edit:  I was accessing the site through the IP number, which I did check using ifconfig to make sure was the same.  I hadn't rebooted the server since yesterday, but I had rebooted the other computer.

---

### Post by dollylamb on 2008-12-02
hi baruch,

i notice that you've had changed server document root to baruch folder then issue a deny from all directive to it without allow directive and i think that's why people can't access your website (403 - NO PERMISSION error). So, i suggest you doing some changes as below:

_ Restore document root to /var/www, then create a virtual folder for baruch using mod alias. If you dont want to do so, just add allow directive to:

<directory />
   deny from all
   allow from your_network/mask
</directory>
to enable people access it.

i attach here my virtual host config file of my apache server. You can take a look at it.

hope that helps.

---

### Post by baruch60610 on 2008-12-02
Hi., Dollylamb:

Thanks again for all your efforts.  I really appreciate it.

I found the problem.  I had changed the permissions of the *target* directory for the symbolic link, removing permission for "other" to execute programs there.  Seemed like a good idea at the time.  For some reason that I'll need to research, this change rendered the whole Website inaccessible.  I was confused by the error messages about symbolic links, and didn't consider the implications of "target not accessible".

Anyway, I do appreciate your efforts.  I still need to reexamine the configuration files and get those "allow" and "disallow" instructions straightened out.  Your comments about those should be helpful.

---

