---
title: "Scripts from /etc/ppp/ip-up.d not run"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by temcat on 2006-11-22
Hi all,

while troubleshooting my PPTP VPN connection on Edgy I found out that for some reason scripts from /etc/ppp/ip-up.d were not run when /etc/ppp/ip-up was executed. I had to save my script as /etc/ppp/ip-up.local - only this way I could get it to run upon connection start.

Nevertheless, the /etc/ppp/ip-up script does contain the following lines:

```
run-parts /etc/ppp/ip-up.d \
  --arg="$1" --arg="$2" --arg="$3" --arg="$4" --arg="$5" --arg="$6"
```

What prevents these from executing? This looks like a bug, but then what package should I file it against?

---

### Post by clessing on 2007-05-21
please check whether /etc/ppp/ip-up.local exists. 
in my /etc/ppp/ip-up, I have 
```

if [ -x /etc/ppp/ip-up.local ]; then
  exec /etc/ppp/ip-up.local "$*"
fi

```
That would exclude /etc/ppp/ip-up.d from being used, because it appears later in the script.

(have a look at "man exec")

---

