---
title: "autoFS and NFS: is it possible to skip and retry later?"
date: 2015-07-26
forum: Networking &amp; Wireless
---

### Post by AllesMeins on 2015-07-26
Hi,

i'm using autoFS to automount some NFS-Shares. For that I created a script, that is called by autoFS which basicly checks, if the server is available - if not it displays a prompt, asking if it should be started.  It works fine, for the most part. The only problem: if I say "don't start the server" autofs counts this as a failed mount attempt ("lookup(program): lookup for ____________ failed) and does not try again mounting that directory later. Is there a way to fix this? Either by a global autofs setting or by something I could return from my script that tells autofs to try it again later...

auto.master

```
# +auto.master

/nfs   /etc/auto.nfs --timeout=300 --ghost
```


auto.nfs
```
#!/bin/sh     

hostname="YYYYYYY"
hwaddr="00:XXXXXXXX"
wolcmd="wakeonlan"

type=$1                                                                                                        
action="101"                                                                                                   
                                                                                               

# Set the display                                                                                              
export DISPLAY=:0                                                                                              
export XAUTHORITY=`ls /var/run/gdm/auth-for-gdm-*/database`
xauth merge $XAUTHORITY                                                                                                                    

while [ $action -ne 102 ]                                                                                      
do                                                                                                             
        #echo "Perform ping"                                                                                    
        ping "$hostname" -nqc1 > /dev/null 2>&1                                                                                        

        if [ $? -eq 0 ] ; then                                                                                 

                #echo "Machine is giving ping response"
                # autofs return                                         
                echo -fstype=nfs4    kodikiste:/ 
		action="102"
		break                                                            

        fi                                                                                                   

        #echo "Displaying xmessage"
        xmessage -buttons "Yes","No" -default "Ja" -center -timeout 1200 -display :0 "Mediaserver offline - Start?"

        action=$?

        if [ $action -eq 101 ] ; then
                #echo "User clicked 'Yes'"

		$wolcmd "$hwaddr" > /dev/null
	        for n in `seq 1 45`; do
			#echo "ping"
			ping "$hostname" -nqc1 > /dev/null 2>&1 && break
			sleep 1
		done

                action="101"

        elif [ $action -eq 1 ] ; then
                #echo "User clicked 'x'"
                action="102"

        fi
done
```

---

