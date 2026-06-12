---
title: "How to read event from shell script"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by mice on 2009-01-30
Hi,

I will like to write a shell script to detect the linux events. Example using the command below:

od -x /dev/input/event1 | tee /var/event.1

It happens that keyboard uses event1. Upon pressing (any) keyboard, the /var/event.1 has 0 bytes contents. It is only when i press keys for 4 times before the /var/event.1 file is filled with 1024 bytes data.

If i simply execute "od -x /dev/input/event1", it will display the events (on screen) whenever i press a key.

1. What is happening? How can i improve it?
2. Is there other alternative to read linux events in shell script?

Thanks in advance.

---

### Post by cmnorton on 2009-02-01
I could not duplicate a lot of what you wrote here, so here are some links:

[http://ubuntuforums.org/showthread.php?t=312882](http://ubuntuforums.org/showthread.php?t=312882)
[https://answers.launchpad.net/ubuntu/+question/51132](https://answers.launchpad.net/ubuntu/+question/51132)
[http://osdir.com/ml/linux.kernel.console/2007-02/msg00004.html](http://osdir.com/ml/linux.kernel.console/2007-02/msg00004.html)

Basically in a shell script, you can test for the presence of a file, whether or not you can read it, and go get the values. I could not get to these directories without being root, so this shell script would have to run as root.

---

### Post by mice on 2009-02-01
Thanks.

I should have provided more details. My intention is to read the keyboard event. 

The first approach i use is to redirect the output of "od" command to a FIFO, and use a "read" command to retrieve the content from thr FIFO.

My script is as below:

rm -f ~/button.1
mkfifo ~/button.1
exec 9<> ~/button.1

# /dev/input/event2 is keyboard events on my system
sudo od -x /dev/input/event2 &

while read event <&9
do
echo ".." $event
done

I expect the "read event <&9" command will return value immediately i press a key. But somehow it doesn't do so until i have pressed keys for several times. It seems like one of the buffer needs a minimum of 1024 bytes to be filled before the "read" successfully.

I will like to make the "od" to dump its value to the FIFO and read the value once a key pressed.

Can someone advise? Thanks again

---

