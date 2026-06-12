---
title: "Trying to figure out networking/communication issues between my laptop and android"
date: 2019-03-07
forum: Networking &amp; Wireless
---

### Post by Mrhihat on 2019-03-07
Hello.

So, I have been trying to get scrcpy to work with my lubuntu laptop. It is a program that allows for display and control of Android devices connected on USB or over TCP/IP.
 Being pretty bad at using the terminal I usually stick to programs with a GUI, but I somehow managed to install it well enough on my computer through some trail and error (doing god knows what damage to my filesystem ;)).

Problem is that it only seems to be receiving data from my phone. I can not use my laptop to control it.
Trying to do anything via the laptop over USB just results with the terminal spitting out the following:

[I]WARN: Unknown event type: 5
WARN: Unknown event type: 5[/I]

I have also tried to activate the TCP/IP wifi function, but I am having no success. This is not surprising as my my tech-wizardry is still weak.
As far as I gathered: You can turn on the wifi by hooking up the phone via USB and typing

**adb tcpip 5555**
**adb connect 142.15.124.7:5555**

in the terminal.
So I thought I should try it out.

This returns:
[B]
adb tcpip 5555[/B]
*restarting in TCP mode port: 5555*

**adb connect 142.15.124.7:5555**
[I]connected to 142.15.124.7:5555

[/I]So, I pull the cable and type **scrcpy** in the terminal to try to launch the app via wifi

this yields:
[100%] /data/local/tmp/scrcpy-server.jar
error: more than one device/emulator
ERROR: "adb reverse" returned with value 1
WARN: 'adb reverse' failed, fallback to 'adb forward'
ERROR: Exception on thread Thread[main,5,main]
java.io.IOException: Connection refused
    at android.net.LocalSocketImpl.connectLocal(Native Method)
    at android.net.LocalSocketImpl.connect(LocalSocketImpl.java:292)
    at android.net.LocalSocket.connect(LocalSocket.java:145)
    at com.genymobile.scrcpy.DesktopConnection.connect(DesktopConnection.java:32)
    at com.genymobile.scrcpy.DesktopConnection.open(DesktopConnection.java:37)
    at com.genymobile.scrcpy.Server.scrcpy(Server.java:13)
    at com.genymobile.scrcpy.Server.main(Server.java:70)
    at com.android.internal.os.RuntimeInit.nativeFinishInit(Native Method)
    at com.android.internal.os.RuntimeInit.main(RuntimeInit.java:286)


help anyone?

---

### Post by Mrhihat on 2019-03-07
Update.

Nevermind folks!
I got it to work.
I used the wrong version of scrcpy-server.jar

---

