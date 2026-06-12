---
title: "Need help with wireless connection"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by tegdirb on 2009-08-19
Hey everyone. 
As an absolute beginner Ubuntu user, I need all the help I can get. I'm not even sure if I'm writing this in the write forum, but I guess I'll just try this time and work it out slowly! hehe! 

Just wondering how I can get my wireless connection to automatically connect or recognize my own wireless address among the list of connections when I want to connect.

I tried changing configurations, to stop the roaming mode, but then it seemed to keep losing the password/changing the password not connecting with the server.... Sorry not to know how to explain the difficulty... 

Can anyone advise me?

---

### Post by Commander_Keen on 2009-08-19
I'm sorry.. I can't figure out what is going on.
Please explain it to me as if I am a 2 year old..

---

### Post by trozombo on 2009-08-19
Do you get actually conection to internet??

---

### Post by tegdirb on 2009-08-19
> **Commander_Keen said:**
> I'm sorry.. I can't figure out what is going on.
Please explain it to me as if I am a 2 year old..
OK, I'll try again!
There is a list of all the wireless connections in the little wireless icon thingy, and my connection is one of them, but the "roaming mode" always selects one of the other connections first, before attempting to connect to my own.  When I select my own connection as the preferred one, it continues to search for the other connections, and sometimes my own connection disappears from the list, and I have to type it in again as "connect to another wireless connection". Usually it eventually connects, but after several attempts and I usually need to re-enter the connection and password again.  

To solve this, I tried to change the configuration and switch off the roaming mode, and when I did this, it indicated that I was connected, but I couldn't open a website "server not found"  So, I switched the roaming mode back on and I continue with the same method, usually resulting in a connection, but not always. 

I hope its a bit clearer now!

Thanks in advance for your help

---

### Post by zkriesse on 2009-08-19
You say it's displaying the list of available connections? And am I correct in understanding that you want it to auto connect? If so here's what you do. Go to System/Preferences/Network Connections. Click Network Connections and it will ask you that it's trying to connect and get the network. If it does just click just once button or ok...if it brings up a menu go to wireless and it should display the list of available networks you have. Click the one you want and click the edit tab on the right side. If it asks for a password enter it. If not then don't worry about it. It should open a menu to edit it and if it does there will be a checkbox for auto connect right under the name of the network name. Check that if you want it to auto connect. Close the menu and then you're done! Hope this helps. Let me know if it did and if you need any more help.

---

### Post by tegdirb on 2009-08-24
Thanks a lot for your help and interest so far!  I have a slight problem with the first step.  When I select System/Preferences I don't  "Network Connections" as a choice in the drop-down menu.  I have something called "Network Proxy", but it seems different from your description. Any advice?  Thanks again in advance!

---

### Post by LewRockwell on 2009-08-24
> **tegdirb said:**
> Thanks a lot for your help and interest so far!  I have a slight problem with the first step.  When I select System/Preferences I don't  "Network Connections" as a choice in the drop-down menu.  I have something called "Network Proxy", but it seems different from your description. Any advice?  Thanks again in advance!

System>Administration>Network Connections

maybe?

.

---

### Post by zkriesse on 2009-08-24
Ok....opposite click on System. Choose the edit menus option. You should see a bunch of stuff with checkboxes. Find the one that says Network Connections. Check it. Hit close and then go to System/Preferences/NetworkConnections. Choose the wirless tab. Pick the connection that you want in wireless and then click edit. Choose the auto connect option then close...close the other stuff and then try to connect to your network. Enter proper password and username and then turn off the pc. Start it up and it should auto connect! Let me know how it turns out.

---

### Post by tegdirb on 2009-09-06
dear friend,  thanks so much for your help so far. Unfortunately, a few weeks later, I'm still trying, but unsucessfully, so thought I would send you the screenshots I have when I try to follow your instructions, to see if you can help me to progress.  It is probably a different version of ubuntu I am using, because I do not have the same "network connections" option as you do. Instead, the same icon is called simply "network" under the "systems-preferences - network" tab.  What do you think.. Can you talk me through this in order to progress further? If not, no worries. Thanks a lot for your time!

---

### Post by Sealbhach on 2009-09-06
Hi, what version of Ubuntu are you using? There was a big change to the Network Manager since 8.10.

.

---

### Post by tegdirb on 2009-09-07
yeah, it's 8.04. I guess it has changed a lot since then?

---

### Post by tegdirb on 2009-09-17
> **Sealbhach said:**
> Hi, what version of Ubuntu are you using? There was a big change to the Network Manager since 8.10.

.
hi there! I'm using ve*rsion 8.04*.  Any advice is welcome ;-)

---

### Post by wilee-nilee on 2009-09-17
You might try right click on the wireless iconhit edit the wireless then delete all of the shown networks. the try logging in like normal by clicking on your wirless signal-enter your password. It may be that in trying to set up the network manager you have it looking at the network with the wrong commands. Here is a great replacement if you have internet access through ethernet. I had problems with Hardy as well and installing this then reinstalling network manger fixed it, but wicd manager is a great usefull program.
 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by tegdirb on 2009-09-23
thanks a lot! I'll give it a go! ;-)

---

### Post by tegdirb on 2009-10-07
> **wilee-nilee said:**
> You might try right click on the wireless iconhit edit the wireless then delete all of the shown networks. the try logging in like normal by clicking on your wirless signal-enter your password. It may be that in trying to set up the network manager you have it looking at the network with the wrong commands. Here is a great replacement if you have internet access through ethernet. I had problems with Hardy as well and installing this then reinstalling network manger fixed it, but wicd manager is a great usefull program.
 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Just wanted to let you know that I think your advice worked! I haven't had a problem since deleting the list of other servers, so I guess that was it! Thanks a lot! Woohoo!

---

