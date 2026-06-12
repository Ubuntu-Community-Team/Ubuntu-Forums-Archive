---
title: "KDE Connect can't see SD card"
date: 2024-05-06
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2024-05-06
In relatively little time I was able to get KDE Connect up and running and solved the issue of being unable to browse the device by appending /storage/emulated/0 to the end of the default browser URL that apparently is a bug in the new KDE Connect.

I can browse through the phone's directories without problem, but what I can't do is get to the files and folders that are on the SD card.  I am guessing that probably this can also be accessed with a different append, but my Hail Mary guesses (such as trying /storage/emulated/1 or /storage/emulated) haven't worked.  

Does anyone know the current (2024) way to access a phones SD card with KDE Connect?

(I am unable to see anything in the KDE Connect App that mentions the SD card, some online instructions indicate this was possible in the past but I am not seeing it.  All I can do is set permissions globally, without choosing the location.)

Thank you for any help!

---

### Post by goemonburo on 2024-05-06
Well, I realized that maybe the easiest way to do this was to take the SD card out, plug it into a card reader, and see what showed up there.  It came up with its ID number, so I plugged (on a hunch) that into the line and it worked.

    /run/user/1000/some_long_hex_string_here/storage/XXXX-XXXX  <-- SD Card
    /run/user/1000/some_long_hex_string_here/storage/emulated/0  <-- Phone internal filesystem

  Hopefully this helps someone else out there!  I've now bookmarked the two locations so all I have to do is make sure the phone's paired, then click on the bookmark.

---

