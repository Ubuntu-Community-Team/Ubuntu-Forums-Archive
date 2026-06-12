---
title: "How to run a command after connecting to network?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by rams123 on 2009-05-10
Everytime I start computer, I do follow things to connect to internet:

* Wait 1-2 sec to let my PC to connect to network. (already adjusted settings in network connections)
* After that I enter a command (**cd Desktop/crclient;./crclient -u rams**) to login. (after this I can access internet).

But it's very hard to do that same thing every time I start PC. So, is there any way to **run that command automatically every time I start PC**?

I know we can add it to startup, but the problem here is, I want to run that command **after** PC has connected to network.

Any idea?

---

### Post by hesjnet on 2009-05-10
You could make a starter link with the command embedded. Right click on the desktop and choose create starter. Insert the command in the appropriate field.

Then you'd only have to double click on the starter when the network is connected.

---

### Post by rams123 on 2009-05-10
OK. I've created a launcher, but little confused what to select there - Application or Location or Application in Terminal?

---

### Post by rams123 on 2009-05-11
Bump

---

### Post by superprash2003 on 2009-05-11
you could use anything..application would be better.. otherwise a terminal would popup whenever you execute it..

---

### Post by Dill on 2009-05-11
Also, it's a bit of a hack, but you could utilize the "sleep" command to execute the command after a given period of time. For instance,

```
sleep 3; echo "Hello, World!"
```

pauses for 3 seconds and then prints "Hello, World!" So if it only takes a few seconds to connect to the network, just try preceding your command with "sleep X", where X is the number of seconds you want to wait.

```
sleep 5; cd Desktop/crclient;./crclient -u rams
```

Perhaps a better way would be to quickly test for a network connection, and, if you're connected, execute the command. Something simple like "ping" could execute the required test...

```
ping_test=`ping -c 2 www.google.com`
if [ $? -eq 0 ]
then
    cd Desktop/crclient;./crclient -u rams
fi
```

Basically, ping returns 0 if it succeeds (if you can successfully get a response from [www.google.com](www.google.com), which means you're connected), and values other than 0 if it fails (different values mean it failed for different reasons). So you can check the return value, and, if it's equal to 0, execute your command. However, you'd want to keep going until you get a value of 0 (that is, you'd want to keep trying until you're actually connected). So you'd want something like this...

```
while [ 0 ]
do
    ping_test=`ping -c 2 www.google.com`
    if [ $? -eq 0 ]
    then     
        cd Desktop/crclient;./crclient -u rams
        break
    fi
done

```

Cheers,
Dill

---

### Post by rams123 on 2009-05-11
**@Dil**: Thanks. I entered **sleep 5; cd Desktop/crclient;./crclient -u rams** in *Terminal* and it's** working**! :)

So, I added the same command in *Startup Applications *and restarted PC. But it's **not working** :( 

==
And I've tried both of your commands and got this result: **./crclient: already logged in with process id 3866**

Screeshot: [[IMG]http://img162.imageshack.us/img162/3223/screenshotterminal.th.png[/IMG]](http://img162.imageshack.us/my.php?image=screenshotterminal.png)

Any idea?

---

### Post by Dill on 2009-05-11
Do you only have the last script set to run at startup? Since you're "already logged in", it seems like you may be running the first script, too. You'll only need to run one or the other at startup -- the latter, which pings Google, is probably preferable.

After you get that error message, does your application still work? That is, are you still logged in? I'd imagine the connection wouldn't fail on account of redundancy. That is, after trying to log in "again", are you connected, or does it kick you off? Either way, make sure you remove the first script (the one that uses "sleep") and just run the second one.

---

### Post by rams123 on 2009-05-11
Thanks for your reply.

Command(sleep 5; cd Desktop/crclient;./crclient -u rams) that I've entered in Starup Apps, isn't working. 

So I've manually entered command(cd Desktop/crclient;./crclient -u rams) in Terminal to login. 

After that I'd tried your command. And got this error, as I said above: **./crclient: already logged in with process id 3866**

[SIZE="1"]==[/SIZE]
I've also tried your both commands **after logging-out**, and got this error: **ping: unknown host [www.google.com](www.google.com)**

==
*[SIZE="1"](Just extra information, leave it if your don't understand)[/SIZE]*
[LIST]
[*]*[SIZE="1"]crclient knowledge base:[http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=](http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=)[/SIZE]*
[*][SIZE="1"]*Also attached crclient folder, just extract tar.gz to get that.*[/SIZE]
[/LIST]

---

### Post by MrWES on 2009-05-11
> **rams123 said:**
> Everytime I start computer, I do follow things to connect to internet:

* Wait 1-2 sec to let my PC to connect to network. (already adjusted settings in network connections)
* After that I enter a command (**cd Desktop/crclient;./crclient -u rams**) to login. (after this I can access internet).

But it's very hard to do that same thing every time I start PC. So, is there any way to **run that command automatically every time I start PC**?

I know we can add it to startup, but the problem here is, I want to run that command **after** PC has connected to network.

Any idea?

I do something simliar; I start conky 30 seconds after my login -- sometimes conky gets hung when starting right at the startup of GNOME.
```
#!/bin/bash
#
# Launch Conky 30 seconds after GDM
sleep 30 && conky &
```
Make sure you make the script executable.
```
chmod u+x scriptname
```
Then you can start it at boot time by calling to it in System | Administration | Startup Applications (in 9.04).

Bill

---

### Post by geirha on 2009-05-11
If you save this script as something like /etc/network/if-up.d/internet-login and make it executable, it will be executed every time a network adapter gets connected.

```

#!/bin/sh

if [ "$IFACE" = "lo" ]; then
    exit 0
fi

/home/*username*/Desktop/crclient/crclient -u rams

```
Make sure to replace *username* with the correct one.

---

### Post by rams123 on 2009-05-11
> **MrWES said:**
> 
```
#!/bin/bash
#
# Launch Conky 30 seconds after GDM
sleep 30 && conky &
```
Make sure you make the script executable.
```
chmod u+x scriptname
```
Then you can start it at boot time by calling to it in System | Administration | Startup Applications (in 9.04).

Bill
woot! It is working! I've created a script with your idea and edited a bit. Now the problem has solved. :guitar:

> **geirha said:**
> If you save this script as something like /etc/network/if-up.d/internet-login and make it executable, it will be executed every time a network adapter gets connected.

```

#!/bin/sh

if [ "$IFACE" = "lo" ]; then
    exit 0
fi

/home/*username*/Desktop/crclient/crclient -u rams

```
Make sure to replace *username* with the correct one.

OK. This looks like pretty good trick, I will try it.

Thanks everyone for your help.

---

### Post by jakobb on 2010-09-10
To answer your original question:
If you are connecting through a wireless connection,
install WiFi Radar and enter the command you want to execute

---

