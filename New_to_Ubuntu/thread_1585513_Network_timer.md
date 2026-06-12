---
title: "Network timer?"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by dudeman4566 on 2010-09-30
In Ubuntu is there a way to set a timer in which your interent will shut off? Cause I might have accidentitly turned it on if so, becuase for some reason after 1 in the morning my intenret stops working

---

### Post by mike555 on 2010-09-30
In most routers there are settings to limit internet..

---

### Post by fugaki on 2010-09-30
You could add a cron job.

For example, you could add an entry:

```
crontab -e
0 1 * * * ifconfig <interface> down
```

When it goes out, just try bringing it back up:

```
sudo ifconfig eth0(or whatever you interface is called) up
```

you can find the interface by running
```

ifconfig
```

and you can look through those entries to see which one you are currently using.

Also, just try a simple reboot. Maybe something is configured to turn the interface down after a specified amount of time, and it just happens to be 0100 each day.

Also, like previously mentioned, you can set access restrictions in the router generally.

---

