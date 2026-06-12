---
title: "Bash Script to launch psql script files"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Vronth on 2009-11-03
Hi, 
(Total newbie bash scripting question.)
Ubuntu 9.10, GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)


I have a heap of psql scripts that I need to run unattended every night.
As far as I can see, there would be two methods for doing this with bash.

Method 1 is to have all the scripts concatenated in one big file and get cron to run it.
(I have done this and it's working.)

Method 2 would be to leave each script in its own file and get bash to run each script.
I would prefer to use Method 2, but I don't know how to set it up.

I have the idea OK, (Cf. the pseudo code below,) but not the syntax.

Any help appreciated.
TIA
Vronth


--- Method 1 ----- All scripts concatenated ------------------

bin/bash
psql

    ## Script 1. orders
    select this, that, the_other from orders
    where x y and z
    group by this
    order by that ;

    ## Script 2. customer bills
    select this, that, the_other from customer_bills
    where x y and z
    group by this
    order by that ;

    ## Script 3. customer_bills and orders stats
    select this, that, the_other from customer_bills, orders
    where x y and z
    group by this
    order by that ;
    
exit psql

--- Method 2 -------- Each script separate ---------------------

bin/bash
psql

    ## Script 1. orders
    run psql 'input file orders.script' 

    ## Script 2. customer bills
    run psql 'input file customer bills.script' 
    
    ## Script 3. customer_bills and orders stats
    run psql 'input file customer_bills and orders stats.script'

exit psql

-------------------------------------------------------------------

---

### Post by yeats on 2009-11-03
Setting up the cron jobs together or separately should be fairly straightforward. 

For the psql command, try:

```
PGUSER=[*database username*] psql [*database name*] -f *filename*
```

If your database host is remote, you can specify it with PGHOST=*hostname or IP* and if the user you use to log in (and to create the cron jobs) is the database user, you can omit the PGUSER part.

Oh, and I'll also mention that you might be a newbie at bash, but bash scripting itself is a bit advanced for the Absolute Beginner Talk forum :-).

---

### Post by Vronth on 2009-11-03
Thanks.
I have disappeared over to bashscripts.org ...
I would like to destroy, delete, remove, kill and purge this post.
Can't find the button for that.

---

### Post by yeats on 2009-11-03
> Thanks.
I have disappeared over to bashscripts.org ...
I would like to destroy, delete, remove, kill and purge this post.
Can't find the button for that. 

Not a way to do it.  All posts are saved by default because *someone* will undoubtedly find them useful at some point. :-)

---

