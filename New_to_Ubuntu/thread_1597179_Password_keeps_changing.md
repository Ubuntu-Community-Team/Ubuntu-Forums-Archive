---
title: "Password keeps changing"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by wordstar on 2010-10-15
Hi there,

I am currenly stayng in my brother's place which has a secure wifi connection.

To connect to the wifi, I have to set ubuntu to connect to a hidden network, then of course put in the prtocol (WEP I think), then put in the password...

My problem is that even after I set the password, on the next reboot, it wont connect.  When the window for the connection comes up and I click on "show password", t will give me this really long string like 66hpe772jdlsjc  something like that.  It works after I correct the password.

My brother says that Ubuntu seems to convert the password into into hex.  Is there a way I can stop ubuntu from converting or changing the password and to keep the original one so that I dont have to keep retyping it all the time?

I am using Ubuntu 8.10 on a PC btw

Thanks

---

### Post by fly-by-night on 2010-10-15
The following is in 10.04, but I think it's similar to what was in 8.10. 

System/Preferences/Network_Connections OR right click the network icon on the panel (taskbar) and select **Edit Connections**.

Select the **Wireless** tab then click on your brother's wireless connection and **Edit**.  Configure all the settings here.  If there's a setting for "Available to all users"(or similar) select that too.  Save and try to connect again.

If there is no connection to select under Wireless, then you need to click New.

Hope it helps.

---

