---
title: "running 2 .sh files together"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by zakiuddin on 2010-06-09
Hello,

I wanted to know if there was any way I could run two .sh files together without using threads??
Something like piping, etc. If yes, please tell me its format.

Awaiting your response,
Zaki.

---

### Post by bodhi.zazen on 2010-06-09
what are you wanting to de ?

cat sh1.sh > shell3.sh
cat sh2.sh >>shell3.sh

#!/bin/bash

commands
more commands

/path/to/sh2.sh

You can also use . , or source


#!/bin/bash
commands
more commands

source /path/to/sh2.sh

#!/bin/bash
commands
more commands

. /path/to/sh2.sh

---

### Post by zakiuddin on 2010-06-09
Thank you for your reply.

I have been using an open source project for first capturing and then decoding data. Both of the files have a .sh extension. But now i want to decode the live data, i.e I want to decode data as soon as i capture it.

Is there any way I can do this without doing threading as it seems to be too difficult to me.

Awaiting your response,
Zaki.

---

### Post by bodhi.zazen on 2010-06-09
> **zakiuddin said:**
> Thank you for your reply.

I have been using an open source project for first capturing and then decoding data. Both of the files have a .sh extension. But now i want to decode the live data, i.e I want to decode data as soon as i capture it.

Is there any way I can do this without doing threading as it seems to be too difficult to me.

Awaiting your response,
Zaki.

IDK

try a pipe

command1.sh | command2.sh

---

### Post by zakiuddin on 2010-06-10
Hello,

Thank you for your reply.

No this command does not work as the capture code first has to make a file in which it stores the data and then the decode code decodes that data. When I run this command it gives "No such file or directory".

Awaiting your response,
Zaki

---

### Post by KIAaze on 2010-06-10
> **zakiuddin said:**
> Hello,

Thank you for your reply.

No this command does not work as the capture code first has to make a file in which it stores the data and then the decode code decodes that data. When I run this command it gives "No such file or directory".

Awaiting your response,
Zaki
Then you have to do it like this:
```
#!/bin/bash
command1.sh
command2.sh

```

And make sure command2.sh looks in the right place for the file it needs.

Note: Actually, if you want to capture and decode streaming data, you will almost certainly have to change your scripts.
```
command1.sh | command2.sh
```
would then indeed be the correct way of doing it.

Can you post your scripts?
It might help.
Also, depending on what you are capturing+decoding, there might already be appropriate tools available.

---

### Post by zakiuddin on 2010-06-10
Thank you for your reply.

The .sh files are "capture.sh" and "go.sh". I have taken them from airprobe project which is used to capture gsm packets. I am pasting them below.

[B]_*CAPTURE.SH*_
[/B]#! /bin/sh

if [ $1"x" = x ]; then
    echo "./capture.sh <freq> [duration==10] [decim==112] [gain==52]"
    echo "Example: ./capture.sh 940.4M"
    exit 1
fi
FREQ=$1

DURATION=$2
if [ $2"x" = x ]; then
    DURATION=10
fi
DECIM=$3
if [ $3"x" = x ]; then
    DECIM=112
fi

GAIN=$4
if [ $4"x" = x ]; then
    GAIN=52
fi


USRP_PROG=usrp_rx_cfile.py
while :; do
    which "$USRP_PROG"
    if [ $? -eq 0 ]; then
        break
    fi
    USRP_PROG=/usr/share/gnuradio/usrp/usrp_rx_cfile.py
    which "$USRP_PROG"
    if [ $? -eq 0 ]; then
        break
    fi

    echo "ERROR: usrp_rx_cfile.py not found. Make sure it's in your PATH!"
    exit 1
done


    FILE="capture_${FREQ}_${DECIM}.cfile"
    samples=`expr 64000000 / $DECIM '*' $DURATION`
    echo "Capturing for $DURATION seconds to $FILE ($samples samples)"
    $USRP_PROG -g $GAIN -d "$DECIM" -f "$FREQ" -N $samples $FILE



[B][U][I]GO.SH

[/I][/U][/B]#! /bin/sh
#echo "go.sh <file.cfile> [decim==112]"

DECIM=$2
FILE=$1

if [ $DECIM"x" = x ]; then
    DECIM=112
fi

./gsm_receive.py  -d "$DECIM" -I "$FILE" | ../../../gsmdecode/src/gsmdecode -i****Awaiting your response,
Zaki.

---

### Post by The Cog on 2010-06-10
Interesting. The only way I can think of doing this is to make a fifo to use as the intermediate file. A fifo can be treated like a file but you can have one process reading from it (even thinking it's a file) and one process writing to it (even thinking it's a file). Try this:

Open two consoles. In one console, make the fifo (we'll just name it my-fifo) like this:
**mknod my-fifo p**
and then begin reading from it, writing anything that comes out to the screen:
**tail -f my-fifo**
Now start a second console and start throwing stuff into it:
[B]echo Hello > my-fifo
ls -l > my-fifo
cat /etc/passwd > my-fifo[/B]

Get the idea? Try having your first script write to my-fifo and your second script read from it. Note that it the second script isn't reading from the fifo, the first script will eventually stall because it can't write any more - fifos have a limited buffering capacity (don't know how big).

---

### Post by zakiuddin on 2010-06-10
Thank you for your reply.

I am sorry I didnt get how to run the commands the way you asked me too. Can you please be a little more elaborate on this i.e. how do I run the .sh files on the commands that you have given me?

Awaiting your response,
Zaki.

---

### Post by The Cog on 2010-06-10
Never mind my last post.

When you say you want them to "run together", do you mean you want the decode to happen immediately after the receive script has finished, or you want the decode to happen concurrently, decoding what has been received so far before the receive program has finished?

If you want them to run one after the other (consecutively) then as KIAaze posted, you need to make up a script (let's call it do-both) with the two commands in it one command on each line, as in > #!/bin/bash
capture.sh
go.sh
you can then make that script executable with **chmod +x do-both**. Then run that script in future.

If you want them to run concurrently, you need to make a fifo much like I said earlier. But looking at the scripts, the first one makes a special file name so you will have to make a pipe file with that name, something like capture_123_456.cfile, so that the capture script writes into that. I would try running the capture process in one window while you run the go process in another to start with, so you can see what they're both up to. If that works, run them concurrently in a script like this:
> #!/bin/bash
capture.sh &
go.sh
Notice the & after the capture command which makes it run in the background so that go.sh is launched woithout waiting for capture to finish.

---

### Post by KIAaze on 2010-06-10
Why not use one script piping the commands together like this ?:

```

#!/bin/bash
# variable defintions & co
...

# main capture+decode commands
$USRP_PROG -g $GAIN -d "$DECIM" -f "$FREQ" -N $samples | ./gsm_receive.py -d "$DECIM" -I | ../../../gsmdecode/src/gsmdecode -iAwaiting your response,

```

edit: i.e. something close to this:
```
#! /bin/sh

####################################################
# variable defintions & co
####################################################

# usage instructions
if [ $1"x" = x ]; then
	SCRIPTNAME=$(basename $0)
	echo "$SCRIPTNAME <freq> [duration==10] [decim==112] [gain==52]"
	echo "Example: $SCRIPTNAME 940.4M"
	exit 1
fi

# argument handling
FREQ=$1

DURATION=$2
if [ $2"x" = x ]; then
DURATION=10
fi
DECIM=$3
if [ $3"x" = x ]; then
DECIM=112
fi

GAIN=$4
if [ $4"x" = x ]; then
GAIN=52
fi

# locate capturing tool
USRP_PROG=usrp_rx_cfile.py
while :; do
	which "$USRP_PROG"
	if [ $? -eq 0 ]; then
		break
	fi
	
	USRP_PROG=/usr/share/gnuradio/usrp/usrp_rx_cfile.py
	which "$USRP_PROG"
	if [ $? -eq 0 ]; then
		break
	fi

	echo "ERROR: usrp_rx_cfile.py not found. Make sure it's in your PATH!"
	exit 1
done

# file not needed anymore
# FILE="capture_${FREQ}_${DECIM}.cfile"

# calculate number of samples
samples=`expr 64000000 / $DECIM '*' $DURATION`
echo "Capturing for $DURATION seconds ($samples samples)"

####################################################
# main capture+decode commands
####################################################
# NOTE: Not sure if the "Awaiting your response," at the end of the command is desired or not. I suppose not. ;)
$USRP_PROG -g $GAIN -d "$DECIM" -f "$FREQ" -N $samples | ./gsm_receive.py -d "$DECIM" -I | ../../../gsmdecode/src/gsmdecode -i
####################################################

```

---

### Post by The Cog on 2010-06-10
It looks like usrp_rx_cfile.py expects a filename to write to, so without tinkering with that python file, I don't think you will be able to get it to write to stdout for easy piping. And I guess the original poster isn't able to modify the wrapper scripts easily either.

---

### Post by KIAaze on 2010-06-10
Yes, I didn't think about that.

Using your fifo file (Very interesting. Thanks. :) ), would it look something like this?:

```
capture.sh FIFO &

while true
do
  go.sh FIFO
done

```

edit:
Untested scripts:

capture.sh
```
#!/bin/sh

if [ $1"x" = x ]; then
echo "$0 <file.cfile> <freq> [duration==10] [decim==112] [gain==52]"
echo "Example: $0 940.4M"
exit 1
fi
FILE=$1
FREQ=$2

DURATION=$3
if [ $3"x" = x ]; then
DURATION=10
fi
DECIM=$4
if [ $4"x" = x ]; then
DECIM=112
fi

GAIN=$5
if [ $5"x" = x ]; then
GAIN=52
fi

USRP_PROG=usrp_rx_cfile.py
while :; do
which "$USRP_PROG"
if [ $? -eq 0 ]; then
break
fi
USRP_PROG=/usr/share/gnuradio/usrp/usrp_rx_cfile.py
which "$USRP_PROG"
if [ $? -eq 0 ]; then
break
fi

echo "ERROR: usrp_rx_cfile.py not found. Make sure it's in your PATH!"
exit 1
done

samples=`expr 64000000 / $DECIM '*' $DURATION`
echo "Capturing for $DURATION seconds to $FILE ($samples samples)"
$USRP_PROG -g $GAIN -d "$DECIM" -f "$FREQ" -N $samples $FILE

```
go.sh
```

#!/bin/sh
#echo "go.sh <file.cfile> [decim==112]"

DECIM=$2
FILE=$1

if [ $DECIM"x" = x ]; then
DECIM=112
fi

./gsm_receive.py -d "$DECIM" -I "$FILE" | ../../../gsmdecode/src/gsmdecode -i

```
do_both.sh
```

#!/bin/bash
	
if [ $1"x" = x ]; then
echo "$0 <fifo.cfifo> <freq> [duration==10] [decim==112] [gain==52]"
echo "Example: $0 940.4M"
exit 1
fi

FIFO=$1
FREQ=$2

DURATION=$3
if [ $3"x" = x ]; then
DURATION=10
fi
DECIM=$4
if [ $4"x" = x ]; then
DECIM=112
fi

GAIN=$5
if [ $5"x" = x ]; then
GAIN=52
fi

mknod $FIFO p

./capture.sh $FIFO $FREQ $DURATION $DECIM $GAIN &

while true
do
		./go.sh $FIFO $DECIM
done

```

---

### Post by The Cog on 2010-06-11
No.

Just more like:
> capture.sh FIFO &
go.sh FIFO
go.sh will never stop - it just blocks when it tries to read more from the pipe, until such times as there is more to read. 

Try the manual example with tail -f that I posted. You don't have to keep running the tail program over and over, because it doesn't exit. It just takes a long time to for the next read from the pipe to return with data. Similarly, go.sh will just freeze mid-analysis until its attempt to read returns another chink of data.

One difference between this and connecting programs with the traditional | command-line piping is that the second program has no way of knowing when it reaches "end of file" because the fifo still exists. You will eventually have to kill the go script. 

Actually, I think if you do it this way round, it might run for the proscribed time and then exit:
> #!/bin/sh

# Start reading from and analysing the FIFO in background (blocks until data available)
go.sh FIFO &

# Start capturing for a while and write to the fifo
capture.sh FIFO

# Sleep for a couple of seconds to give go.sh time to analyse 
# the last bit of data that capture wrote
sleep 2

---

