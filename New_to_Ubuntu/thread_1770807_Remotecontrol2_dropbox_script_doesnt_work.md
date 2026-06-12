---
title: "Remotecontrol2 dropbox script doesnt work"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by niekverw on 2011-05-29
I'm trying to get a script to remotely control ubuntu via dropbox to work in bash, 
I copy/past it into a .sh and then run it in the terminal but i get alot of errors like 

> remote.sh: 23: Syntax error: "(" unexpected (expecting "}")

 does anyone know how i can get it to work? 

The script from [http://wiki.dropbox.com/TipsAndTricks/RemoteControl2](http://wiki.dropbox.com/TipsAndTricks/RemoteControl2)
```
#!/bin/bash

cmdDir=~/Dropbox/remote
cmdFile=$cmdDir/in
logFile=$cmdDir/output/out

server()
{
    > $logFile

    # Wait for command file to show up and send it to running bash
    inotifywait -m -q -e close_write,moved_to --format "%w%f" $cmdDir | while read file
    do
        [[ $file = $cmdFile ]] || continue
        cat $file
    done | /bin/bash -i >> $logFile 2>&1
}

client()
{
    local lastSize=$(stat -c %s $logFile)
    local size=$lastSize
    local wheel=("|" "/" "-" "\\\\")  # Spinning wheel
    # Force a prompt at start to confirm connection
    local line=": $RANDOM"               

    while [[ -n $line ]] || read line
    do
        # Send command
        echo "$line" > $cmdFile

        # Wait for output
        echo -n "Waiting...."
        let i=0
        while [[ $size -eq $lastSize ]]
        do
            # Should really use inotifywait here but it doesn't seem to work
            # with the way Dropbox updates $logFile.
            sleep 0.5
            echo -n -e "${wheel[$i]}\b"
            let i=(i+1)%4
            size=$(stat -c %s $logFile)
        done

        # Display output
        if [[ $size -lt $lastSize ]]
        then
            echo "Error; please try again"
        else
            echo -n -e "\r            \r"
            tail -c $((size - lastSize)) $logFile
        fi

        lastSize=$size
        line=
    done
}

if [[ $1 = "-s" ]]
then
    server
else
    client 
fi 
```

---

