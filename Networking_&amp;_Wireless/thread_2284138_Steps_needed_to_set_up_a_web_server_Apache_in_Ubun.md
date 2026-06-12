---
title: "Steps needed to set up a web server Apache in Ubuntu desktop"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-06-27
Hello!
                              
                              I'm running Ubuntu 14.04 desktop ed. I'm  about to set up LAMP. I wonder what would be the correct order of steps  that should be taken. I've alredy got a static IP from my ISP. 
                              
                              My idea would be as such:
                              1) To set up a static IP in Ubuntu and router. To cancel DHCP in both Ubuntu and the router;
                              2) To configure a Firewall in Ubuntu;
                              3) To update registrar's DNS entries for  my domain name (hostname). I already has both the registrar and my  site's domain name. To input my ISP's two DNS servers' IP's and to  update my hostname's A record by inputting my static IP into it.  Probably I should also update other records if needed CNAME for www. and  MX for MTA;
                              4) To install LAMP stack (I would need  HTTPS, so do I need to make sure that Open SSL is being installed too OR  it's done automatically by default?);
                              5) To place my script's files (in my case  it's Joomla) into an approprate Apache's folder (probably www, I think);
                              6) To set up SSL on Apache.

---

### Post by TheFu on 2015-06-27
Sounds like you have most of it correct. Lots of details missing, but that is normal at this stage.  Don't forget to forward the single port (443/tcp) from the WAN to the LAN on the router.  Never use the "DMZ" mode on a router.  I've never used the ISP's DNS servers.

I keep registrar, DNS, hosting with 3 different organizations. Makes it harder for any 1 of them to "steal my traffic."

Take careful notes, take daily backups, be certain you read about security and security best practices and securing joomla (it would suck to be hacked in the first few hours running a test server).  
Before you deal with LAMP ... [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
You don't need any MTA and I wouldn't run any MTA (that allowed inbound connections) on the same machine as I ran other high-risk processes like apache.  Running an in/out MTA is more dangerous than running a web server, IMHO, and there are millions of currently hacked web servers on the internet - just think of all the phishing emails that have URLs inside them ... every one of those URLs point to a hacked web server.

I would setup normal http (80/tcp) first, then find specific instructions to run https ... might be worth considering running a reverse proxy if you plan to run multiple, different, backend web services.  That way the SSL cert you buy won't be holding you back from swapping to a faster web server later.  Apache is sorta the "kitchen sink" of web servers, so it isn't the lightest or the fastest.

Please be aware that with 14.04 and later, the version of Apache changed in Ubuntu - so be certain any instructions you follow are for that apache version.
Also - you might want to use mariaDB instead of mysql. There are many reasons, some technical, but most are political, IMHO.

[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) should have the step-by-step instructions you need.
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla) - Joomla
[https://www.howtoforge.com/how-to-install-joomla-on-ubuntu-14.04](https://www.howtoforge.com/how-to-install-joomla-on-ubuntu-14.04) - usually the best step-by-step guides, but double-check the security.
[https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup](https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup) -  platform security specific to Joomla
[https://docs.joomla.org/Security_Checklist/Joomla!_Setup](https://docs.joomla.org/Security_Checklist/Joomla!_Setup) - and finally Joomla security

Also, please be aware that running "server" on a system with a desktop is slightly less secure. X11 (X, sometimes called X/Windows) and any GUI is a security consideration for all internet facing systems.  It is best to NOT run a GUI on a server for a few reasons.  However, we all do it when first starting out.

BTW, there is a "Server" sub-forum which is probably a better place to ask these sorts of questions.

Anyway - good luck. Have fun, and please do versioned, daily, backups.  This is the #1 systems, security and just "save-your-butt" technique.

---

