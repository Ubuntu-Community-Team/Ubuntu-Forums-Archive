---
title: "Connecting to the Internet via USB from WM6 PDA"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by indigoparadox on 2008-10-26
I've found tons of HOWTOs detailing how to connect to the Internet *through* a Windows Mobile-based phone and some (costly) wireless Internet service. What I want to do is connect to the Internet *through* my Ubuntu Hardy-based PC *from* my Windows Mobile-based phone, preferably via USB.

That is, on my phone, I want to be able to view web pages in IE (not so important) and, more importantly, run the Windows Mobile Funambol client (very, very important--SynCE isn't quite there yet!) when the phone is in its cradle.

Is there something obvious I'm missing here?

---

### Post by mperry on 2008-10-26
I just did this actually. I have a HP IPAQ 110 which is just a pocket PC and no phone. It does have wifi. Here is what I did:

1) Follow the guide for synce installation at [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

2) Be sure to add the packages it recommends. Ignore the steps about rndis0 mode since that's the way you tether a device and use the mobile device's connection on the laptop and not the way you want to do it. You need to get the tools in place though no matter what. You may need the syncegnome tool if there is a password on the device though. I did. Now you can also copy files, delete things, get directory listings on the device which is pretty handy.

3) Browse to the synce-engine page on the wiki at [http://www.synce.org/moin/SynceSetup/SyncEngine](http://www.synce.org/moin/SynceSetup/SyncEngine). You need to setup syncengine the way it says on that page. I had to download the config.xml file to get it to work. 

4) Now you should be ready to run the actual tool which shares the laptop network connection with the device. Be sure you have setup a partnership. One word of warning here. I wanted to use the exchange activesync partnership on the device already and I got into a problem using it when I had installed an new partnership that did Calendars and Contacts using the create partnership thing on ubuntu. I erased that old partnership using the command "synce-delete-partnership" command and that will delete partnerships on the device as well as on the host.

Just run the synce-sync-engine command with the mobile device hooked up. You'll see a whole bunch of output in the terminal window. Go to the mobile device and launch something like IE mobile. Should work now.  Just so you know, I tried this any number of more complex way for a day and just did not read the syncengine page for whatever reason. You may have to go back and ensure that everything just runs according to the pages I referenced; but I can now synchronize to my exchange server at work, work on the internet with the device on USB using my laptop's network connection, copy files back and forth.

Very nice.

---

### Post by indigoparadox on 2008-10-28
Indeed, I didn't realize that the Internet connection was active while sync-engine was running.

It works beautifully. Thank you very much!

---

