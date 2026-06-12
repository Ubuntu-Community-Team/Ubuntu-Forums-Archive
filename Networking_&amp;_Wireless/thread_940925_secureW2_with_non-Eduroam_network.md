---
title: "secureW2 with non-Eduroam network"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by mishterbeaver on 2008-10-07
Hello,

I'm a student at the University of Pennsylvania and I've freshly installed Ubuntu 8.04. Connecting to our wireless network requires installation of SecureW2, which still does not support linux. Searching through these forums I found many students in Europe have this same problem, and were able to resolve it with various configurations which have not worked with me in the network manager. 

I have found the pre-configuration .inf file that my school includes with its build of SecureW2, but searching through my system has not uncovered any .cer or .der files stored locally. There is a VerifyServerCertificate = TRUE option in the .inf and a TrustedRootCA.0 thumbprint value, but it seems that there is no information pointing to a local certificate on my machine.

I set in Network Manager the SSID, WPA Enterprise. Then I followed the .inf configuration to set TTLS, WEP, and PAP (configuration looks very similar to that of these Eduroam users). However, entering my username and password with these options does not result in a connection (though the signal is detected & at good strength). The only disparities I see between the .inf setup and net manager is that .inf sets authentication type to "open" and the .inf specifies the server address with which to verify a server certificate fingerprint, neither of which options do I know how to set in Ubuntu net manager. (However I don't know if any of those settings are needed).

What could SecureW2 be doing on my Windows installation that the network manager is not currently setup for??

Any help is greatly appreciated!

---

### Post by willca on 2008-10-08
does your school have the instructions online for this?
it will help if i can see what they need for a windows xp to do to connect.

---

### Post by mishterbeaver on 2008-10-08
[http://www.upenn.edu/computing/wireless/configure/windows/xpvista.html](http://www.upenn.edu/computing/wireless/configure/windows/xpvista.html)

This is the windows config info. All that I did for Vista was install this secureW2 program and restart my computer. The wireless network is detected before the install but you cannot authenticate with your user name and password without installing this program.

I'm attaching the .inf file that came with the windows installation as a .txt so you can see the whole thing if it helps.

---

### Post by novicetopro on 2008-10-27
I having the same issue connecting to my university wireless. My school uses TTLS with PAP (inner) with a certificate. I have searched and searched for the last month and this seems like an issue that hasn't really solved. There isn't any instructions anywhere that helps. SecureW2 makes this really easy on Vista, I don't understand why Ubuntu doesn't have this working. 

Does anyone have any idea how to fix this? This issue is the main reason I am still using my Vista partition over my Ubuntu partition. 

I am on Intrepid beta, It didn't work in hardy either. I upgraded cause I read somewhere it may have been fixed in Intrepid

---

