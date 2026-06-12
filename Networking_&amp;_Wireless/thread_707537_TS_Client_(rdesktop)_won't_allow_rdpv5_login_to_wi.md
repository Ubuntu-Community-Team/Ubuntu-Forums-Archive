---
title: "TS Client (rdesktop) won't allow rdpv5 login to win server (it used to work)"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by mikesf on 2008-02-25
i use tslcient (ubuntu 7.07) to rdesktop to a win server. it worked perfectly until a few days ago. after the win login screen (on the server) flashes briefly, it gives me the error:

Autoselected keyboard map en-us disconnect: No valid license available.

---

### Post by SpaceTeddy on 2008-02-25
is this a windows 2003 server ? if so, they windows 2003 servers have the terminal server installed via a 90 day evaluation period. If you want to use it afterwards, you need to reset the terminal server (turn it off) and turn on normal rdesktop logins.

It's been two years since i touched a windows server... so forgive me if i am a but shaky on the details... but as far as i know, this is not an ubuntu problem, but one with the windows server :(

---

### Post by mikesf on 2008-02-25
i found a temporary solution ...

to take care of the first part of the error message, it was necessary to add the "en-us" keyboard type one of the tabs of the tsclient gui (i don't know how i missed this). alternatively, one could pass the option rdesktop -k en-us serverName to accomplish the same thing.

as for the other part of the error,..the windows server was just failing to recognize me for some bizaar reason. QUICK FIX??? just add my ip address to the "client" field on the first page of the gui. (my hostname is not recognized by the winsux server for some reason).

let me point out that we asked for a computational server running linux, but they gave us winsux... oh well... perhaps these things could be avoided if everyone just played nice. thanx again, bill gates! i'm continuously amazed at the 'performance' i get with winsux.

---

### Post by gurps on 2008-02-28
Hi, I had the same problem and I found that Windows wants a differente client name different after x days. So I use rdesktop with the option -n <clientname> and everything seems to work !
Bye

---

