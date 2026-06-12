---
title: "Resume X Forward over SSH"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by Skerit on 2008-03-19
X forwarding runs just fine over SSH, I love it, but is there a way to let the applications run should I shut down my client pc? (And VNC isn't an option)

I would like to use this for torrents, have deluge running on my server while seeing the application on my client. When I shut the PC down deluge should keep on running.

When I start the client again the original existing deluge should  open, not a new one ...

Or is this asking too much? Is it even possible to recover applications when the SSH connection fails?

---

### Post by finer recliner on 2008-03-19
as far as i know, when you close an SSH connection, it closes any processes that you started from there. there's no way around it.

---

### Post by walmartshopper67 on 2008-03-19
There is a great program for this called screen.

on the command line logged in to your remote machine at the prompt, type screen, and that will open a screen session, where you can run your programs (like bittorrent, which is  what i use for the most). to disconnect, type 'ctrl A' then 'd') and that will disconnect from the screen session. now you can log off your remote connection and your torrent will run. Next time you log in, type 'screen -r' and you can re-attach to that session.

for more, type 'man screen' and have lots of fun!

---

### Post by Skerit on 2008-03-23
Oh,that's what I need, thanks!

I heard about screen before but I must have misunderstood it's explanation.

Thanks!

Edit: Errr, I think I understood it quite well, screen is for command-line programs, it's of no use for any X-forwarding

---

