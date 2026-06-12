---
title: "cron job scheduled bash script won't open GTK window"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Herschdorfer on 2011-07-28
Dear community,

i want to check if an application is running an reopen it if needed. the script works and outputs my comments to the syslog via logger. 

i tried to use this commands to open a GTK window from the bash:

```
export DISPLAY=:0.0	
/opt/c2g/Home_Displa &>> /var/log/Home_Display.log &
```

that works fine if i run the script as user or sudo. but doesn't work if the cron job executes the script.

what's wrong?

greetings,
herschdorfer

---

### Post by androssofer on 2011-07-28
> **Herschdorfer said:**
> Dear community,

i want to check if an application is running an reopen it if needed. the script works and outputs my comments to the syslog via logger. 

i tried to use this commands to open a GTK window from the bash:

```
export DISPLAY=:0.0	
/opt/c2g/Home_Displa &>> /var/log/Home_Display.log &
```

that works fine if i run the script as user or sudo. but doesn't work if the cron job executes the script.

what's wrong?

greetings,
herschdorfer

could b it needs root permission?

i've had to add a few jobs to roots crontab to get stuff to work.. perhaps worth a try?

EDIT: read this part as just "run as sudo": > as user or sudo
so scrap tht plan

try:

```
export DISPLAY=:0 && /opt/c2g/Home_Displa &>> /var/log/Home_Display.log
```

---

### Post by Herschdorfer on 2011-07-28
Thanks for the reply!

i found out that if i use the crontab of my user, not the root crontab, this line works 

```
export DISPLAY=:0 && /opt/c2g/Home_Display &
```

with this in line in crontab

```
* * * * * /opt/c2g/check_HD_app
```

---

