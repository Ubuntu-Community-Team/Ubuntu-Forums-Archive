---
title: "netcat bot"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by trigsenior on 2009-10-11
```

#/bin/bash

password="123456"
user ="Mre"
ouput="/tmp/ouput"
rm -f output
echo "" > output
tail -f output |nc -l -p 2000|
    while true
    do read LINE || break


if [[ $LINE = "help" ]]; then
        echo "UPTIME" >> output
        echo "DATE" >> output
        echo "PING" >> output
        echo "CLEAR" >> output
        echo "----Admin-----"
        echo "login password  REBOOT" >> output
        echo "login password  SHUTDOWN" >> output
        echo "login password  EXIT" >> output
        echo "login password  LOGIN " >> output
fi

if [[ $LINE = "LOGIN $user $password"  ]]; then
               echo "Welcome Mre" >> output
               echo "-----------" >> output
               echo "run ......." >> output       
               /bin/sh >> output 
fi

if [[ $LINE = "UPTIME"  ]]; then
       echo "uptime is; $(uptime)" >> output
fi

if [[ $LINE = "DATE"  ]]; then
       echo "date is; $(date)" >> output
fi     

if [[ $LINE = "PING"  ]]; then 
       echo "Ping $(ping -t 5  $LINE)" >> output
fi

if [[ $LINE = "CLEAR"  ]]; then
        echo "Done $(rm -f output)" >> output
fi


if [[ $LINE = "LOGIN $user $password REBOOT"  ]]; then
         echo "Rebooting $(reboot)"  >> output
fi

if [[ $LINE = "LOGIN $user $password SHUTDOWN" ]]; then
         echo "Shutdown $(shutdown -h now)"  >> output
fi

if [[ $LINE = "LOGIN $user $password exit" ]]; then
         echo "bye bye  $(killall nc)"  >> output
fi

done

```


Been playing around with netcat and bash , Managed to get it working very simple =( 

Couple questions 


I don't like repeating fi , can i have multiple if statements so

```


if [[ $LINE = "blah"  ]]; then 
       blah

[[ $LINE = "blah"  ]]; then 
       blah
else

   echo "blah not found"

fi

done


```

No idea why this does not work.

```

if [[ $LINE = "PING"  ]]; then 
       echo "Ping $(ping -t 5  $LINE)" >> output
fi

```


any tips / improvements would be great =)

---

