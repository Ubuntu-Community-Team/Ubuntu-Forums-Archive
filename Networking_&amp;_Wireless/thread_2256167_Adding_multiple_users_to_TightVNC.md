---
title: "Adding multiple users to TightVNC"
date: 2014-12-10
forum: Networking &amp; Wireless
---

### Post by ndnd on 2014-12-10
Hello all,
I have been able to successfully instal tightvncserver on the server end (UBuntu LTS 12) and tightvncviewer on client end (Windows 8). It all works fine without any problems I am able to connect and open GUI applications. 

Now I wish to add more users and am following the instructions as per the link and getting some errors


[http://www.tecmint.com/install-tightvnc-remote-desktop/]("http://www.tecmint.com/install-tightvnc-remote-desktop/")

This worked till I setup more users and gave password to their accounts. 

However, the problem starts in configuring of the tighvncserver file  located at 
/usr/bin/ 

Now I have copied the exact syntax for the file (from the link - I am pasting the same below 

Script I added at the bottom of the file 

[PHP]## Multiple Users ##
  VNCSERVERS = "1:user1 2:user2";
  VNCSERVERARGS[1] = "-geometry 1280x1024";
  VNCSERVERARGS[2] = "-geometry 1280x1024";

[/PHP]

The error I am getting 
> Can't modify constant item in scalar assignment at /usr/bin/tightvncserver line 780, near ""1:user1 2:user2";"
syntax error at /usr/bin/tightvncserver line 781, near "VNCSERVERARGS["
Execution of /usr/bin/tightvncserver aborted due to compilation errors.


I believe there is also inconsistency in the documentation for e.g I need the ';' which was not mentioned and the location of the file was different than what was stated in the website. 

So maybe this varies from version to version or there is some error or steps are missing. 

In case someone has a good link, I can read that and implement it as well. I am sure I am missing out on the syntax here. 

Thanks in advance!

---

### Post by steeldriver on 2014-12-10
try removing the spaces around the = in your variable assignments

```

## Multiple Users ##
  VNCSERVERS="1:user1 2:user2"
  VNCSERVERARGS[1]="-geometry 1280x1024"
  VNCSERVERARGS[2]="-geometry 1280x1024"  

```

---

