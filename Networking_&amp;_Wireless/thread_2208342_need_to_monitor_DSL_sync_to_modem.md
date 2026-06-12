---
title: "need to monitor DSL sync to modem"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2014-02-27
I have been having issues with my DSL modem losing sync with the network for several years. AT&T has replaced everything and keeps telling me there is nothing wrong. Never mind the fact that I can watch the status go up and down. I finally convinced them to take a closer look based on a script I wrote to log the drops:

```

#!/bin/bash
while [ 1 ]
tput clear
echo "DSL Modem Sync Monitor"

do
   tput cup 3 1
   ping IP_ADDRESS -c 1

   if [ $? -eq 0 ]
   then
        tput cup 12 1
        echo "Sync Condition Normal"
        tput el
      sleep 1s
   else
      COUNT=1
      LOOP=0

      while [ $LOOP -le 10 ]
      do
           tput cup 12 1
           echo "Packet Loss $COUNT Out Of 10"
           tput el

         sleep 1s
         tput cup 3 1 
         ping 68.16.218.4 -c 1

         if [ $? -ne 0 ]
         then         
            let COUNT=COUNT+1
         fi

         let LOOP=LOOP+1
      done
      
      if [ $COUNT -ge "10" ]
      then 
         date >> sync.error
           tput cup 12 1
           echo "Sync Error Ocurred"
           tput el
         sleep 1s
      fi
   fi
done

```

This worked great until today when the replaced my Netopia modem with a Netgear. Now the script is no longer able to ping the IP address. I tried using [www.google.com](www.google.com) as the IP address, but for some reason that wasn't very reliable either. If no one knows who to get the modem to stop blocking that ping request, is there a program or script that will do this same thing?

Thanks....

---

