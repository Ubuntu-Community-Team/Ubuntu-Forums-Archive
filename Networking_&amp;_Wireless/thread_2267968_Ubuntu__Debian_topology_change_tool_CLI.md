---
title: "Ubuntu / Debian topology change tool CLI"
date: 2015-03-05
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2015-03-05
Hi all
Is their a command line based tool for Ubuntu / Debian that can show topology changes i a network between a source and destination.
So when a topology change happends (source takes a different path to destination) it prints such info to the terminal screen.

Thanks on advance
Kind regards

---

### Post by Lars Noodén on 2015-03-05
The closest might be [traceroute](http://linux.die.net/man/8/traceroute) or traceroute6.  They operate from the shell but have to be installed explicitly.

---

### Post by Drenriza on 2015-03-05
I tried using 
```
traceroute --mtu
```
and
```
tracepath
```

Which i am currently playing around with, thanks for the reply

---

### Post by Lars Noodén on 2015-03-05
You have to point traceroute at a particular target

```

traceroute --mtu 8.8.8.8

```

It won't tell you the topology itself but will give you an idea of the route that those particular packets happened to take on that one occasion.

---

### Post by Drenriza on 2015-03-06
Thanks for the reply Lars

I putted together a small script and are wondering how this can be improved.
Which i have _**NO**_ doubt it can be :) My bash skills is extreamly rusty

```

#!/bin/bash

##This script looks for changes in the topology, from a source to a destination target.
##If a change happends it will be printed to the screen of the device that runs the script.

##The script takes two arguments [destination_target], [sleep_between_traceroutes]

if [[ $EUID -ne 0 ]]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

destination_target=${1}
sleep_between_traceroutes=${2}
run="1"

path1="/tmp/topologyChange1.txt"
path2="/tmp/topologyChange2.txt"

file1="0"

count="0"

echo "script start up"
if [ -e ${path1} ]; then
    rm -v ${path1}
fi

if [ -e ${path2} ]; then
    rm -v ${path2}
fi
while [ ${run} -eq 1 ]
do
    let "count++"
    echo "Script has runned ${count} times"
    if [ ${file1} -eq 0 ]; then
        traceroute -n -I ${destination_target} |awk '{print $2}' |sed '1d' > ${path1}
        file1="1"
    else
        traceroute -n -I ${destination_target} |awk '{print $2}' |sed '1d '> ${path2}        
    fi

    if [ -e ${path1} ] && [ -e ${path2} ]; then
        
        echo "checking topology"    
        if [[ ! $(diff -s ${path1} ${path2}) == "Files /tmp/topologyChange1.txt and /tmp/topologyChange2.txt are identical" ]]; then
            clear
            echo "topology has changed"

            diff -y ${path1} ${path2}

            mv ${path2} ${path1}
        else
            echo "no topology change"
            echo ""
        fi
    
    fi

    sleep ${sleep_between_traceroutes}
done

exit 0

```

---

### Post by Lars Noodén on 2015-03-06
I see that you could use just awk and do not need sed also.  There are several ways to do that.  One would be to check if the second column starts with a digit.

```

 awk '$2 ~ /^[0-9]/ {print $2}'

```

You might ask over on the Development & Programming subcategory for other tips.

---

