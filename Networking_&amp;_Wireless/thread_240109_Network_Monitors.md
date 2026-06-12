---
title: "Network Monitors"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by ice60 on 2006-08-20
for some reason i spend alot of time playing around with network monitors. i found this page, maybe someone will find it useful?? i know i'll come back and look through the software mentioned.
[http://planetmy.com/blog/?p=148](http://planetmy.com/blog/?p=148)

i've got these nice aliases i use too, the first too update every second, but you can change that if you like:

# netstat
alias net='watch --interval=1 "sudo netstat -apn -l -A inet"'
alias net2='watch --interval=1 "sudo netstat -an --inet --inet6"'
alias net3='sudo lsof -i'
alias net4='sudo netstat -ano -l -A inet'

---

