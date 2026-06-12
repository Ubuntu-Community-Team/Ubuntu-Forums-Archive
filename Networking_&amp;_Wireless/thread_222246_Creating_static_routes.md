---
title: "Creating static routes"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by h20Boodle on 2006-07-24
Can anyone please tell me how static routes are permanently added and enabled in Dapper? In my Hoary machine I have "up route add ..." statements in the /etc/network/interfaces file, so I know that what I have works in Hoary, but putting the same statements into the Dapper machine's /etc/network/interfaces file simply doesn't work.

---

### Post by h20Boodle on 2006-07-24
In the words of Rosanna Rosanna Danna, "Nevermind." I found that my ordering of statements in the /etc/network/interfaces file was wrong. After I corrected it, it started working just as it had in Hoary. My only beef now is that unless a person knows about the /etc/network/interfaces file, they won't have a clue how/where to set a static route.

---

### Post by h20Boodle on 2006-07-25
Okay, so maybe I spoke too soon. Today when I started the computer the routing tables were just fine and I was a happy camper. However, I shut off the computer to go to lunch, and when I came back and started the computer, the routes were all wrong again. 

I looked through the /var/log/messages and debug files, looking for clues as to why it's not working, but I can't find anything that would indicate that setting up the routes failed.

Anyone have any ideas? 

I'm also looking for a way to restart the networking services without rebooting. I tried "/etc/init.d/networking restart", but it just hangs.

Thanks.

---

