---
title: "Ubuntu slow in torrent downloading?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by computerandu on 2011-06-25
I have felt it numerous times. When I use Ubuntu for downloading from Torrents it hardly goes to 200 Kbps but if I download the same torrent in Windows it easily goes around 600-800Kbps....quite fast in Windows....

Any idea why it happens? I have set no limits on downloading and uploading rates, have a huge list of trackers in Transmission bit client...but nothing helps....2-3 Hours in Windows helps me in downloading all the files....but I don't want to go to Windows to download ....

Also, when i download in Ubuntu, the files are named as .part (eg. filename.avi.part) till the time they are finished downloading....while its not the same case in Windows...where it is kept as it is...any thoughts on that folks...

---

### Post by Abir Valg on 2011-06-25
My thoughts would be trying various torrent clients on linux to see if this behaviour is consistent among them.
Also maybe your ethernet/wifi driver is the bottleneck which is slowing you down.
Even though it is avi.part, you can still play that file in VLC.
If you don't like .part, uncheck "Append part.." in Preferences->Torrents
Also there is a default limit in Transmission, i believe it's
maximum peers per torrent 60
maximum peers overall 240
This can be increased.
Cheers.

---

### Post by Alwimo on 2011-06-25
This is how to raise the limits Abir Valg referenced.

When in Transmission, select Edit, then Preferences, then Network.

Down the bottom of that window, you can raise or lower the limits.

---

### Post by haqking on 2011-06-25
> **computerandu said:**
> I have felt it numerous times. When I use Ubuntu for downloading from Torrents it hardly goes to 200 Kbps but if I download the same torrent in Windows it easily goes around 600-800Kbps....quite fast in Windows....

Any idea why it happens? I have set no limits on downloading and uploading rates, have a huge list of trackers in Transmission bit client...but nothing helps....2-3 Hours in Windows helps me in downloading all the files....but I don't want to go to Windows to download ....

Also, when i download in Ubuntu, the files are named as .part (eg. filename.avi.part) till the time they are finished downloading....while its not the same case in Windows...where it is kept as it is...any thoughts on that folks...

by default transmissions uses a different port to say bittorrent which may be your windows client which uses 6881
I take it your router is setup with port forwarding and if so needs to be set up for the port you are using in transmission or whatever Linux client you end up using.

and make sure Upnp is enabled on your router and also if you have the linux firewall running make sure you have a rule set up to allow it on the given port etc.

i suspect transmission is using a different port than you have set up on your router....but im guessing, if you havent got port forwarding set up then you should have anyways

---

### Post by westie457 on 2011-06-25
> I have set no limits on downloading and uploading rates

Try throttling your up-load speed to about 5-10 % of your total speed. Too high an up-load speed reduces the band-width available for down-loads. Hope this helps.

If it does not then 'hacqing' is probably right. Personally I have had no problems with the default settings in Transmission or my router.
Whether running in Ubuntu or Vuze in Windows I am using default settings.

---

### Post by computerandu on 2011-06-25
Thanks everyone for your suggestions...I'll try each one of them and then will come back to the thread with my findings....till then the thread is open.....

More suggestions are also welcomed...

---

### Post by hawthornso23 on 2011-06-25
Read up on the issue of bufferbloat.

If this is the problem the fix is to limit the upload speed to prevent the outgoing buffers in your network from filling up. With unlimited upload speed these buffers quickly fill introducing a network lag of up to several seconds in the outgoing direction. Since this lag also effects TCP control packets, it plays merry hell with your download speed as well. Experimentation is needed to find the rate which works best.You want to limit your rate to just below the maximum throughput of your network so that the buffers don't fill.

Edit: Older versions of windows limited themselves to 64k of data `on the fly'. This made them inherently less likely to trigger this problem.

---

### Post by fractalman on 2011-06-25
I use 'Deluge' for torrents, never had an issue with the download speed.

---

