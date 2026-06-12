---
title: "Synergy problems"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by re2851 on 2010-02-19
hello all, 

I'm having some issues with synergy.  I had it running fine for a while on an ubuntu computer and a vista computer.  No problems.  But i recently acquired an old laptop that was running very sluggish with vista so i put ubuntu on it as well.  I want to use the laptop as a server with the client being my other ubuntu computer and leave the vista computer with it's own keyboard and mouse.  I have tried everything but get the same message everytime.  I added the file and configured everything.  The file configures on the server fine.  but when i start the client (named Ryan), it gives me the following message on the server computer:

```
NOTE: CClientListener.cpp,127: accepted client connection
DEBUG: CClientProxy1_0.cpp,404: received client "Ryan" info shape=0,0 1440x900
WARNING: CServer.cpp,266: a client with name "Ryan" is not in the map
NOTE: CServer.cpp,1909: disconnecting client "Ryan"
NOTE: CClientProxy1_0.cpp,206: client "Ryan" has disconnected
```

The client comes up with a similar message:

```
NOTE: synergyc.cpp,330: started client
ERROR: CServerProxy.cpp,188: server refused client with name "Ryan"
WARNING: synergyc.cpp,265: failed to connect to server: server refused client with our name
```

I read up on the synergy page that this means i forgot to put the client in the map.  But it's there. the synergy.conf file reads:

```

section: screens
	laptop:
	Ryan:
end
section: links
	laptop:
		right = Ryan
	Ryan:
		left = laptop
end
```

I'm not sure what to do.  I've tried everything.  I tried using ip addresses and using Ryan.local cause it said something on the site about it might be adding that or something. I'm just not sure what else to try.  Did i do the file wrong?  "Ryan" was the name that i used to link the vista computer to it and it worked fine.  I thought maybe that the laptop can't find Ryan in the network or something because when i set up the original link between vista and ubuntu i had to get it so that "Ryan" was visible on the network for vista.  Any suggestions would be greatly appreciated!  Thanks in advance for any help!

---

### Post by audiomick on 2010-02-19
Hi.
The file looks right. Here is mine. It is for three computers. ubuntu-desktop (ubuntu 9.10) is the server. Right of that is vista-laptop (Vista, obviously), right of that is vera-laptop (ubuntu 9.10). 

I have to use the IP of ubuntu-desktop to get in with the Vista machine.

Have you tried using a lower case R fro Ryan? I don't know if it makes any difference really, but have a vague memory of it being relevant for something to do with computer names.
```
section: screens
ubuntu-desktop:
vera-laptop:
vista-laptop:
end

section: links
 ubuntu-desktop:
  right = vista-laptop
 vera-laptop:
  left = vista-laptop
 vista-laptop:
  left = ubuntu-desktop 
  right = vera-laptop
end
```

---

