---
title: "Mount windows shares with special chars in names"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by aduran on 2008-11-03
Helo all. I have a problem that i could not resolver for the whole day.

Facts:
- I have a windows box with a network share named like "Informática" (notice the á)
- Ubuntu connects to it seamlessly when done through the GUI
- I am unable to do the same from command-line, in fstab
- Reading on the internet, they say that you can use special chars, like spaces, using octal like this: "my\040share"
- Looking at wireshark to see wthat is going on, i see that when it works, it looks for the folder "Inform\301tica.
- Looking again when done trough fstab and it's looks the samen when i put in fstab:
//host/Inform\301tica
it seems to do the same like before, but it does not work, although the share's name asked for is the same.
Also the are some options that differ from one packet to another, like de Dfs flag.

I have been searching the internet and trying things the whole day, with no luck.
Any pointers will be very appreciated.
Thanks!!

Greetings,
Antonio

---

