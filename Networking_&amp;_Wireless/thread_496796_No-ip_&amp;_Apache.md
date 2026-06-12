---
title: "No-ip &amp; Apache"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by lolikapuxa on 2007-07-09
I need to access my website from the outside, with a no-ip adress.
 But if i put my ip in the browser, it makes me go to my router settings page.

  How can i send outside people to my website in spite of sending them to the router page?

---

### Post by lolikapuxa on 2007-07-09
Hey i solved this problem.

Actually, people from the outside are using my site. Just don't know why, but when i try to access it via ip address it shows me my router page... but fine... as long as the others can view it.

---

### Post by scxtt on 2007-07-09
generally you can't use your WAN ip from within your own network ... i've had cases where it doesn't work and cases where it does - might be a router thing ...

---

### Post by Norst on 2007-07-10
For me it was a router thing. With my Linksys it was fine but when I changed to new DSL the router they provided me would just take me to the router. A way around this was to edit the /etc/hosts file to point at my server for certain domain names.

For example I have a web server on my network locally at 192.168.2.80, lets say I have a site running on it called [www.mysite.com](www.mysite.com), if I typed that in my browser it would take me to the router. but if I add to my hosts file (/ect/hosts):
192.168.2.80 [www.mysite.com](www.mysite.com)

then when I type [www.mysite.com](www.mysite.com) in my browser it will point directly to the server and not try to go to the router. (note that after the change to the hosts file the browser would have to be closed and relaunched).

Hope this helps.

---

