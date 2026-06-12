---
title: "Remote X Applications (Solaris 10) are Too Slow"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by sandbagger2000 on 2008-06-10
I frequently connect to a remote machine that runs Solaris 10 and run X client applications. I tunnel X through ssh -Y to make the connections.

Running under Ubuntu, X is far less responsive than for other distributions or OS's.  I ran some experiments by repeatedly launching the GNU "insight" debugger, using two different machines on my home network (one a desktop with a wired connection, the other a laptop over wireless) using a variety of different techniques. The results are amzingly consistent. Ubuntu & Kubuntu take nearly 5 times as long to finish bringing up the initial windows as almost anything else I tried:

The following consistently take 150 seconds, plus or minus 10:
  Desktop, Ubuntu Hardy installed
  Desktop, Kubuntu Hardy from live CD
  Laptop, Ubuntu Hardy in Wubi
  Laptop, Ubuntu Gutsy in vmware player hosted on Windows XP

The following take 30 seconds, plus or minus 5:
  Desktop, openSUSE from live CD
  Desktop, Puppy from live CD
  Laptop, XMing under Windows XP
  Laptop, Puppy from live CD
  
The above illustrates what I had felt intuitively - remote X applications in general were sluggish enough on my "working machine", the Hardy desktop, that I'm starting to avoid using it.  I have a suspicion, but can't confirm, that this timing problem became a lot worse after the remote machine was upgraded from Solaris 9 to Solaris 10 about a month ago.

I know that X is very sensitive to latency timing, so I tried disabling IPV6 on the desktop machine running Hardy. That had no effect on the above timing.

Any suggestions on why the Ubuntu family would perform so badly at this, and how I can fix it?

---

### Post by sandbagger2000 on 2008-06-12
A followup: confimed this difference in timing with CygWin/X and Mandriva Linux. Ubuntu is consitently 5 times slower than any other X server I can find.

Checking the system monitors for Ubunto and a couple of these other cases shows that, in fact, Ubuntu is both sending and receiving 4 to 5 times as many bytes as others. That certainly explains the timing, but now the question is why Ubuntu's traffic is so much higher.

---

### Post by lswb on 2008-06-12
I'm just taking a wild guess here, but could you try it with NetworkManager disabled?

:wq

---

### Post by sandbagger2000 on 2008-06-14
Thanks, **lswb**. It's an interesting thought. But, no, disabling the Network Manager has no effect.

I'm now thinking that this is not a low-level networking issue. I repeated the test on one of my two Ubuntu installations where I happened to have VirtualBox installed. The "native" Ubuntu was slow as reported above. Then from inside that Ubuntu session, I launched VirtualBox, running Mandriva as a guest, connecting to the network by NAT via the Ubuntu host. The virtual machine ran as fast as any of the the others I have reported.

Now, unless I misunderstand, all of its basic networking is still being handled through Ubuntu. Since it runs significantly faster, the difference must be at a higher level. My suspicion is that the Ubuntu X is requesting redraws of the entire Window way too often, maybe every time a new widget arrives from the remote machine. Not sure how to check this, though.

---

### Post by Woei on 2008-06-16
> **sandbagger2000 said:**
> I frequently connect to a remote machine that runs Solaris 10 and run X client applications. I tunnel X through ssh -Y to make the connections.

Running under Ubuntu, X is far less responsive than for other distributions or OS's.  I ran some experiments by repeatedly launching the GNU "insight" debugger, using two different machines on my home network (one a desktop with a wired connection, the other a laptop over wireless) using a variety of different techniques. The results are amzingly consistent. Ubuntu & Kubuntu take nearly 5 times as long to finish bringing up the initial windows as almost anything else I tried:

The following consistently take 150 seconds, plus or minus 10:
  Desktop, Ubuntu Hardy installed
  Desktop, Kubuntu Hardy from live CD
  Laptop, Ubuntu Hardy in Wubi
  Laptop, Ubuntu Gutsy in vmware player hosted on Windows XP

The following take 30 seconds, plus or minus 5:
  Desktop, openSUSE from live CD
  Desktop, Puppy from live CD
  Laptop, XMing under Windows XP
  Laptop, Puppy from live CD
  
The above illustrates what I had felt intuitively - remote X applications in general were sluggish enough on my "working machine", the Hardy desktop, that I'm starting to avoid using it.  I have a suspicion, but can't confirm, that this timing problem became a lot worse after the remote machine was upgraded from Solaris 9 to Solaris 10 about a month ago.

I know that X is very sensitive to latency timing, so I tried disabling IPV6 on the desktop machine running Hardy. That had no effect on the above timing.

Any suggestions on why the Ubuntu family would perform so badly at this, and how I can fix it?

I had a similar experience with plain X11 network traffic between a NetBSD 4.0 box and a Fedora 8 box. Throughput was fine at 12MByte/sec on a 100Mbit switched network, so that wasn't the problem. I eventually tracked it down to the TCP_NODELAY flag that can be set on TCP sockets and its particularly bad interaction with the Naggle algorithm. Without TCP_NODELAY, modern TCP/IP networking stacks will delay (up to 40ms or more) sending out ACK packets to received TCP segments for a very good reason. Imagine an interactive application where you receive some input and want to generate a response. When you receive the input, you could either immediately send an ACK that you received the data, *or* you could wait sending out the ACK, create your response, and **piggyback** the ACK together with your response. Because there's an overhead of 40 bytes for the combined TCP and IPv4 header, you'll want to cut back on the number of tiny (1 byte ACKs) packets sent out, because a 1-byte response results in 40 bytes of TCP/IP overhead.

The Nagle algorithm works as follows: when you have outstanding data sent that isn't ACKed yet by the other end, the TCP/IP stack buffers data delivered to it by the user process up to the maximum segment size determined during TCP's three-way handshake or until the other side ACKs your outstanding data. Again, this is good idea in general so as to avoid sending lots of tiny packets over poor network links with lots of packet loss. However, because the other side is using delayed ACKs, the Nagle algorithm is buffering up user data in the TCP/IP stack until the other end ACKs the data after an (unneeded) delay or until the mss of 1460 bytes (which is typical for ethernet LANs) is reached.

If you're moving your mouse around on a forwarded X desktop, this creates a torrent of small XEvent packets to update the mouse position. The X11 protocol is a very efficient binary protocol which minimizes the size of the packets that need to be sent between X11 clients and their X11 server. If you have Nagle's algorithm on the X11 server interacting with an X11 client which uses delayed ACKs, you'll have the TCP/IP stack on the client batching up the ACKs to the updated mouse position. This in turn will make the X11 server wait pushing out more data to the client, because the XEvent for the updated mouse position hasn't been ACKed yet.

Therefore, I have added the following options to /etc/sysconf.conf, on both the client and server:

```

net.ipv4.tcp_low_latency = 1
net.ipv4.tcp_dsack=0
net.ipv4.tcp_congestion_control=reno

```

The [FONT="Courier New"]tcp_low_latency[/FONT] option disables the delayed ACK-algorithm. This will result in lower peak throughput, but will help very much in the latency department. X11 connections are usually bound by their latency rather than throughput. For bulk file transfer over NFS or SMB, it's usually the other way around.

That's also one of the reasons why X11-forwarding over fat internet pipes or even high quality WIFI-links is usually very sluggish: while you can reach 2Mbyte/sec over such links, it's the roundtrip time, the latency between sending a packet and receiving an acknowledgement thereof that's limiting a good X11-experience.

You also say that you're using SSH tunneling. That's fine over networks you can't physically protect. However, if you want to do X11 forwarding at home on a LAN that remains between your premises and you don't have people you don't trust use the network, then you're far better off using untunneled X11. Sure, all keystrokes are sent as raw X11 packets over the network, thereby exposing your passwords. But if there will be noone on your network running a packet sniffer, then the added latency and CPU overhead can be safely avoided. If you still insist on using SSH tunneling, I'd advice using a cipher that's less resource intensive, like RC4 instead of AES. You'd do something like '[FONT="Courier New"]ssh -c arcfour -Y somehost[/FONT]', or add a snippet like this to your[FONT="Courier New"] ~/.ssh/config[/FONT] file:

```
Host foobar.lan
    Compression no
    Ciphers arcfour
    ForwardAgent yes
    ForwardX11 yes
    ForwardX11Trusted yes
```

As an added bonus, untunneled X11 allows you to use XDMCP so you can have a nice login screen that starts a full blown desktop session instead of starting your apps one by one from a shell over SSH.

---

### Post by sandbagger2000 on 2008-06-17
**woel**, I don't have control over the remote client, but I tried the sysconf.conf changed you suggested on my local server with no visible effect.  That does not entirely surprise me. As I understand the effect of Nagle's algorithm, it will delay sending ACKs, which could lead to longer delays between packets. But I'm actually seeing a proportionally large increase in the amount of data begin transferred, not the same amount of data being sent over a longer period of time.
 Nor is the increased traffic due to a flurry of mouse notifications - for the purpose of doing this timing I kept hands off the mouse and keyboard from the moment I hit enter to launch the program to the moment that it finally rendered the window. I'm still stumped.

---

### Post by timcredible on 2008-06-17
is it possible to make the connection without the ssh tunneling?  if you use a direct connection, then you could use wireshark and see what's going on with all those extra packets.  you could also check the update manager and see if there are any updates relating to xdm or gdm.  do you use Xnest to access the server, or are you running each app separately?

---

### Post by sandbagger2000 on 2008-06-29
My various Ubuntu installations were all fully updated. I am not using xnest but running the applications separately.

I have run wireshark now on two systems using a direct X connection, Ubuntu Hardy Heron and CygWin/X. To keep things simple, I used a small application that opens a window with a single label and a single button:
[FONT="Courier New"]#!/usr/local/bin/perl
#!/usr/local/bin/perl
use Tk;
    use strict;

    my $mw = MainWindow->new;
    $mw->Label(-text => 'Hello, world!')->pack;
    $mw->Button(
        -text    => 'Quit',
        -command => sub { exit },
    )->pack;
    MainLoop;
[/FONT]
I set wireshark to capture communications on port 6000.

Even for this small application, Ubuntu exchanged significantly more packets (170) than CygWin/X (130). 

I'm not enough of an expert to interpret these traces at a detailed level. Here is the [Ubuntu trace]("http://www.cs.odu.edu/~zeil/temp/ubuntu_smallwin.txt") and here is the [CygWin/X trace]("http://www.cs.odu.edu/~zeil/temp/cygx-smallwin.txt"). Perhaps someone could give these a quick look and let me know if there is anything obviously wrong or if there's some other kind of information I should be looking at?  Thanks.

---

### Post by carrawae on 2008-09-19
I have essentially the same problem described by sandbagger.  In my case, I do have control of both sides of the connection (Ubuntu SSH server to CentOS SSH client) and tried the suggested mod to sysctl.conf and it made no difference.

I do not see the problem on my Redhat box, so I am pretty sure it's an Ubuntu issue. (Ubuntu 8.04 on a Dell 1525).

Throughput is around 200kB/s from CentOS machine to both the Ubuntu and Redhat systems.

How do we report this as a bug to the developers?

---

### Post by timcredible on 2008-09-19
edit: nevermind

---

### Post by CnlPepper on 2008-11-04
There is an open bug report on this exact issue, please add your names to it so the devs so a bit more interest!

[https://bugs.launchpad.net/ubuntu/+bug/241063](https://bugs.launchpad.net/ubuntu/+bug/241063)

---

