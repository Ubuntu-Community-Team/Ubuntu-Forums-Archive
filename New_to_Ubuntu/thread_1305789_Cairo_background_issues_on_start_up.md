---
title: "Cairo background issues on start up"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Biggs1338 on 2009-10-30
I have been playing around with Ubuntu 8.10 for about a month now. I have set my Cairo-dock to run automatically on start up. However, when it starts automatically, the background is black. When I start it manually, it is transparent. I would like it to start with a transparent background automatically. Any suggestions would help. I tried looking into the configuration settings but could not decipher anything that helped. BTW, Ubuntu Intrepid is now my favorite OS. So much flexibility and such a great community!

---

### Post by fabounet on 2009-10-30
I suggest you to start the dock with a delay
with a command like
sleep 10 && cairo-dock -o (or -c if you start without OpenGL)

---

