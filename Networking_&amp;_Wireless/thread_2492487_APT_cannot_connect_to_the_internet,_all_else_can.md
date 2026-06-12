---
title: "APT cannot connect to the internet, all else can"
date: 2023-11-13
forum: Networking &amp; Wireless
---

### Post by masterrabbit on 2023-11-13
Hello all, and thanks in advance for your assistance:

I am trying to do a deep dive into Linux and Ubuntu. I'm almost exclusively, otherwise, a Mac person. I am running Ubuntu using Parallels Desktop on am M1 MacBook Pro with Touchbar.

In order to help me learn the components of Linux and Ubuntu, and because I'm a stickler for security, I decided to experiment in implementing Lynis and USG/CIS audits and fixes, typically going point by point and manually fixing the OS configurations, to improve the security of my VM. The internet works when using any and all applications, except one very important one: APT from the terminal. I do now know what specifically broke this, otherwise I'd basically know how to fix it (by reversing what I did incorrectly). I am specifically trying to run do-release-upgrade. I should note, also, that Software Updater cannot resolve the repositories either.

 When inputting 'sudo ip link show,' I get the following:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 96:0b:73:fd:2d:0f brd ff:ff:ff:ff:ff:ff permaddr 00:1c:42:7c:3b:c5
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:ba:fb:ad:1f brd ff:ff:ff:ff:ff:ff

```
 
 When inputting 'sudo systemctl status NetworkManager,' I get the following:

```
&#9679; NetworkManager.service - Network Manager     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-11-13 02:17:28 CST; 18min ago
       Docs: man:NetworkManager(8)
   Main PID: 1049 (NetworkManager)
      Tasks: 3 (limit: 2185)
     Memory: 4.9M
        CPU: 220ms
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1049 /usr/sbin/NetworkManager --no-daemon


Nov 13 02:17:30 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863450.0657] device (docker0): state change: prepare >
Nov 13 02:17:30 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863450.0658] device (docker0): state change: config ->
Nov 13 02:17:30 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863450.0659] device (docker0): state change: ip-confi>
Nov 13 02:17:30 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863450.0706] device (docker0): state change: ip-check>
Nov 13 02:17:30 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863450.0707] device (docker0): state change: secondar>
Nov 13 02:17:30 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863450.0711] device (docker0): Activation: successful>
Nov 13 02:17:33 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863453.1107] agent-manager: agent[aa9f08fc0f755611,:1>
Nov 13 02:17:45 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863465.1124] agent-manager: agent[9199eccd857097d0,:1>
Nov 13 02:25:55 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699863955.5386] agent-manager: agent[39810b33cbb5082b,:1>
Nov 13 02:32:29 ubuntu-linux-22-04-02-desktop NetworkManager[1049]: <info>  [1699864349.2764] dhcp4 (enp0s5): state changed new lease,>

```

I've disabled UFW to see whether that may help.

On my MacBook Pro, running macOS Sonoma, I use Little Snitch and have the OS firewall set to block all incoming with stealth (drop ICMP requests). However, I've set Little Snitch to silent (allow connections) and tried turning off the OS firewall. No luck.

The error that I get from do-release-upgrade is:

```
Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

```

I also get a bunch of errors saying that certain repositions are listed in sources.list multiple times. (That isn't true, however. Each repository is listed twice, but once as an amd64 repository and once as an arm64 repository. The specific lines that is refers to as replicative are the proposed release repositories, whereas the first are the stable repositories. So, I'm not sure where this error comes from.) In either case, that wouldn't prevent Ubuntu from downloading the packages. Each repository gives an error 404.

Any thoughts? I am not sure what else to provide to help diagnose.

---

### Post by ian-weisser on 2023-11-13
Please show us the actual (and complete) output of "sudo apt update"

---

### Post by masterrabbit on 2023-11-13
Sure.

```
parallels@ubuntu-linux-22-04-02-desktop:~$ sudo apt update[sudo] password for parallels: 
Hit:1 https://download.docker.com/linux/ubuntu jammy InRelease
Hit:2 https://repo.protonvpn.com/debian stable InRelease
Get:3 http://ports.ubuntu.com/ubuntu-ports lunar InRelease [267 kB]
Get:4 http://ports.ubuntu.com/ubuntu-ports lunar-updates InRelease [109 kB]
Get:5 http://ports.ubuntu.com/ubuntu-ports lunar/main arm64 Packages [1372 kB]
Get:6 http://ports.ubuntu.com/ubuntu-ports lunar/main Translation-en [513 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports lunar/main arm64 DEP-11 Metadata [442 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports lunar/main DEP-11 48x48 Icons [107 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports lunar/main DEP-11 64x64 Icons [158 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports lunar/main DEP-11 64x64@2 Icons [21.1 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports lunar/restricted arm64 Packages [77.6 kB]
Get:12 http://ports.ubuntu.com/ubuntu-ports lunar/restricted Translation-en [21.9 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages [143 kB]
Ign:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages
Ign:26 http://ports.ubuntu.com/ubuntu-ports lunar/main amd64 Packages
Ign:27 http://ports.ubuntu.com/ubuntu-ports lunar/universe amd64 Packages
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages [236 kB]
Ign:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages
Ign:26 http://ports.ubuntu.com/ubuntu-ports lunar/main amd64 Packages
Ign:45 http://ports.ubuntu.com/ubuntu-ports lunar-updates/restricted amd64 Packages
Ign:46 http://ports.ubuntu.com/ubuntu-ports lunar-updates/main amd64 Packages
Ign:47 http://ports.ubuntu.com/ubuntu-ports lunar-updates/universe amd64 Packages
Ign:48 http://ports.ubuntu.com/ubuntu-ports lunar-updates/multiverse amd64 Packages
Ign:27 http://ports.ubuntu.com/ubuntu-ports lunar/universe amd64 Packages
Ign:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages
Ign:26 http://ports.ubuntu.com/ubuntu-ports lunar/main amd64 Packages
Ign:45 http://ports.ubuntu.com/ubuntu-ports lunar-updates/restricted amd64 Packages
Ign:46 http://ports.ubuntu.com/ubuntu-ports lunar-updates/main amd64 Packages
Ign:47 http://ports.ubuntu.com/ubuntu-ports lunar-updates/universe amd64 Packages
Ign:48 http://ports.ubuntu.com/ubuntu-ports lunar-updates/multiverse amd64 Packages
Ign:27 http://ports.ubuntu.com/ubuntu-ports lunar/universe amd64 Packages
Ign:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages
Ign:26 http://ports.ubuntu.com/ubuntu-ports lunar/main amd64 Packages
Ign:45 http://ports.ubuntu.com/ubuntu-ports lunar-updates/restricted amd64 Packages
Ign:46 http://ports.ubuntu.com/ubuntu-ports lunar-updates/main amd64 Packages
Ign:47 http://ports.ubuntu.com/ubuntu-ports lunar-updates/universe amd64 Packages
Ign:48 http://ports.ubuntu.com/ubuntu-ports lunar-updates/multiverse amd64 Packages
Ign:27 http://ports.ubuntu.com/ubuntu-ports lunar/universe amd64 Packages      
Ign:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages
Ign:26 http://ports.ubuntu.com/ubuntu-ports lunar/main amd64 Packages
Ign:45 http://ports.ubuntu.com/ubuntu-ports lunar-updates/restricted amd64 Packages
Ign:46 http://ports.ubuntu.com/ubuntu-ports lunar-updates/main amd64 Packages
Ign:47 http://ports.ubuntu.com/ubuntu-ports lunar-updates/universe amd64 Packages
Ign:48 http://ports.ubuntu.com/ubuntu-ports lunar-updates/multiverse amd64 Packages
Ign:27 http://ports.ubuntu.com/ubuntu-ports lunar/universe amd64 Packages      
Ign:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages
Err:13 http://ports.ubuntu.com/ubuntu-ports lunar/restricted amd64 Packages
  404  Not Found [IP: 185.125.190.36 80]
Ign:26 http://ports.ubuntu.com/ubuntu-ports lunar/main amd64 Packages
Ign:45 http://ports.ubuntu.com/ubuntu-ports lunar-updates/restricted amd64 Packages
Ign:46 http://ports.ubuntu.com/ubuntu-ports lunar-updates/main amd64 Packages
Ign:47 http://ports.ubuntu.com/ubuntu-ports lunar-updates/universe amd64 Packages
Ign:48 http://ports.ubuntu.com/ubuntu-ports lunar-updates/multiverse amd64 Packages
Ign:27 http://ports.ubuntu.com/ubuntu-ports lunar/universe amd64 Packages
Ign:28 http://ports.ubuntu.com/ubuntu-ports lunar/multiverse amd64 Packages  
Err:45 http://ports.ubuntu.com/ubuntu-ports lunar-updates/restricted amd64 Packages
  404  Not Found [IP: 185.125.190.36 80]
Ign:46 http://ports.ubuntu.com/ubuntu-ports lunar-updates/main amd64 Packages
Ign:47 http://ports.ubuntu.com/ubuntu-ports lunar-updates/universe amd64 Packages
Ign:48 http://ports.ubuntu.com/ubuntu-ports lunar-updates/multiverse amd64 Packages
Fetched 375 kB in 4s (87.9 kB/s)
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11 (universe/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11 (multiverse/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (restricted/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11 (universe/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11 (multiverse/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
Reading package lists... Done
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11 (universe/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11 (multiverse/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (restricted/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11 (universe/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11 (multiverse/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/lunar/restricted/binary-amd64/Packages  404  Not Found [IP: 185.125.190.36 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/lunar-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 185.125.190.36 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:4
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11 (universe/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:17
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11 (multiverse/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:29
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (restricted/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:10
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11 (universe/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:19 and /etc/apt/sources.list:20
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11 (multiverse/dep11/Components-arm64.yml) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:31 and /etc/apt/sources.list:32



```

---

### Post by masterrabbit on 2023-11-13
Here's the feedback from 'sudo do-release-upgrade -p':

[https://pastebin.ubuntu.com/p/8M5YWyhRKY/](https://pastebin.ubuntu.com/p/8M5YWyhRKY/)

---

### Post by TheFu on 2023-11-13
It looks like no networking is configured, but let's check.

From inside the VM, can you run 
```
ping -c 4 1.1.1.1

```
and 

```
ping -c 4  google.com

```
Show your work.

I know very little about MacOS besides is based on BSD.  I know less about Parallels, but in most hypervisors, there are 4 different types of networking that can be setup for each VM.  Since no IP is provided to your VM (see the 'ip' command?), I'm guessing you didn't setup the VM networking to meet your needs.  Typically, people use either "NAT" for the VM or "bridge".  In some hypervisor software, this is controlled via a checkbox in the Networking tab to pick 1 type of network.

With NAT, the hypervisor would place the VM onto a NAT'd subnet, different from any other, and have an internal DHCP server that sets up the IP and gateway and routing outside the VM.  Nobody else can take to the VM in this configuration.

With Bridge mode, the hypervisor would share the existing NIC from the host OS to the VM. The VM would use the DHCP server on the regular LAN - the same DHCP that the hostOS and other LAN devices use.  Outside traffic would be able to access the assigned IP to the VM and the host firewall shouldn't have any impact at all.  If you want a firewall for Linux, you'd need to set that up under the Linux VM.

---

### Post by masterrabbit on 2023-11-13
This is interesting...

```
$ ping -c 4 1.1.1.1bash: ping: command not found

```

Parallels has a Parallels Tools add-on that you install after first initiating the VM. With the exception of often needing to change NetworkManager.conf to allow managed network interfaces, the Tools sets up the network to generally work. I think the first case (NAT) is operative. For instance, in my resolve.conf on macOS, it placed the VM in a subnet in the 127.0.0.0/8 range. My home network is in the 192.168.1.0/32 range. However, the docker0 interface is a bridge connection.

I always set up the UFW to allow in on lo, allow out on lo, deny in from 127.0.0.0/8, and deny in from ::1. I don't know what any of that means, except CIS Benchmarks recommends it. Secondarily, I deny all incoming, which I do understand. However, I've disabled the firewall completely for troubleshooting purposes.

---

### Post by ian-weisser on 2023-11-13
ports.ubuntu.com does not have amd64
Use a different mirror for that architecture.

---

### Post by masterrabbit on 2023-11-13
So, this is what my Advanced Connections looks like.

[IMG]https://i.ibb.co/wJkff9X/Screenshot-2023-11-13-at-9-26-49-AM.png[/IMG]

[IMG]https://i.ibb.co/X2jJf3w/Screenshot-2023-11-13-at-9-26-33-AM.png[/IMG]



[IMG]https://i.ibb.co/gDgb57v/Screenshot-2023-11-13-at-9-27-08-AM.png[/IMG]

[IMG]https://i.ibb.co/Sx0v8Cw/Screenshot-2023-11-13-at-9-26-04-AM.png[/IMG]

[IMG]https://i.ibb.co/fDbBRxS/Screenshot-2023-11-13-at-9-26-57-AM.png[/IMG]


[IMG]https://i.ibb.co/KmhsvRM/Screenshot-2023-11-13-at-9-26-15-AM.png[/IMG]

The only reason I'm not concerned about the interfaces is that, presumably, HTTPS and APT requests use the same interface. If there was an issue with the setup of the interfaces, I wouldn't be able to access the internet in Firefox. But I can. Also, to ensure that it wasn't Little Snitch on macOS messing up the APT requests, I spun up a new VM with a fresh Ubuntu install. APT worked without a hitch. 

So, there must be some config file that APT uses and Firefox doesn't that is causing the requests to fail?

---

### Post by masterrabbit on 2023-11-13
P.S.,

To be sure, I deleted both my interfaces ('docker0' and wired). I then rebooted and reinstalled Parallels Tools. Parallels Tools does things like sets up your network, adds network printers, etc. I then rebooted again. It re-setup those exact same interfaces. Internet works, same error when running 'sudo apt update/upgrade' and 'sudo do-release-upgrade -p'.

---

### Post by masterrabbit on 2023-11-13
P.P.S.,

Thanks so much for your help, in advance.

---

### Post by TheFu on 2023-11-13
Please don't post huge images with text output easily provides the requested information.  Some people pay for internet by the byte.  Also, docker networking isn't related and is actually a bit funky.
Did you **ping** the things requested?

How is it that Apple doesn't include ping?  That's just dumb. 
```
$ ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=53 time=44.5 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=53 time=17.9 ms
```

**deny in from 127.0.0.0/8** will prevent name resolution via systemd-resolved on Ubuntu from working.  systemd-resolved causes issues for some people. It is a replacement for resolvconf which also caused some people issues.  I found both to be useless in my situation, but I have DNS servers on my LAN and don't want/need those extra things screwing up my name resolution.

I don't use the stock Firefix, but some years ago, firefox started using their own DNS by default and called it "security".  I disable their DNS (it broke my internal DNS use) to avoid Mozilla being a MiTM for all my web traffic and DNS lookups. I suppose we get to choose who we trust when there aren't many good choices available.  I hate it when programs decide to ignore using system settings for important things.  MSFT started this, Google added it to Android, then Chrome, and it seems FireFox decided their DNSSec/DNS-o-HTTP was better for us than using OS services.  I think MSFT may have stopped (don't really know, as I don't use MSFT OSes on any networks).  The Android change screwed me for some time, forcing me to setup a LAN DNS - thanks google.  When Firefox added it, I knew quickly because none of my LAN servers could be accessed, just internet servers.  DNS. Know it. Use it. Love it.

BTW, details matter. I suspect you don't really mean resolve.conf - that file doesn't exist on any Unix-like OS.  It is resolv.conf.

To quickly test if name resolution is the issue, put this line at the top of your /etc/resolv.conf file:
```
nameserver 1.1.1.1
```
above all other lines.  If that solves the APT issue, for the next 10 minutes (or until systemd-resolved decides to refresh settings, then it is a name resolution issue. At reboot, systemd-resolved will force it back to the default, unless you disable and mask that service.  On Ubuntu, resolvconf has been deprecated for 3+, perhaps 7 years.  I used to purge both resolvconf and systemd-resolved packages to regain control over my DNS ... I'd also purge avahi because it was breaking somethings too.  Avahi is the Linux ZeroConf implementation of mDNS.  Is has some uses (like making driverless printer setup a non-event) and I suppose it is useful for people who don't need/want an internal DNS.  For the first few years that Avahi was inflicted onto Linux users, it was terrible, often using 100% of CPU on a system before it crashed.  I haven't seen or heard of that issue in over 10 yrs, however.  There is a quirk with Avahi - the names that have to be used are {hostname}.local .... so if your hostname is joes-pc, other systems on the LAN would need to access it as "joes-pc.local".  Also, I don't know of any Linux server install that includes avahi. It can be added, but it isn't part of the normal install dependencies.  Just something else to consider.

---

### Post by masterrabbit on 2023-11-13
Sorry, you said to use ping from inside the VM. macOS does include ping. In either case, I was able to install ping on the Ubuntu vm. The printout is as follows:

```

$ ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=128 time=25.4 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=128 time=22.7 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=128 time=32.0 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=128 time=19.7 ms
^Z
[3]+  Stopped                 ping 1.1.1.1


$ ping -c 4 google.com
PING google.com (142.250.189.14) 56(84) bytes of data.
64 bytes from lax31s16-in-f14.1e100.net (142.250.189.14): icmp_seq=1 ttl=128 time=57.6 ms
64 bytes from lax31s16-in-f14.1e100.net (142.250.189.14): icmp_seq=2 ttl=128 time=54.8 ms
64 bytes from lax31s16-in-f14.1e100.net (142.250.189.14): icmp_seq=3 ttl=128 time=67.2 ms
64 bytes from lax31s16-in-f14.1e100.net (142.250.189.14): icmp_seq=4 ttl=128 time=57.0 ms


--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 54.783/59.151/67.224/4.777 ms

```

 resolv.conf was setup with a nameserver in the 127.0.0.0/8 range. I overrode that, as suggested, but no dice.

I'm going to reinstall macOS over my existing setup to repair the system fils. That shouldn't be an issue because I just spun up a new Ubuntu vm with working APT, but without my other configurations. But it won't hurt to try.

---

### Post by masterrabbit on 2023-11-13
I reinstalled macOS on my host system to repair any system files that may be quirky. No change in VM behavior.

The only other thing I can think of is that either Stacer or Bleachbit system 'cleaning' botched something. I think it ceased working shortly after installing and running them.

---

### Post by TheFu on 2023-11-13
I've never used Stacer or Bleachbit.  Maybe 15 yrs ago, Bleachbit was helpful, but since around 2015, I get the feeling it causes more problems than it fixes.  I'm not a fan of add-on tools that make claims to do stuff on a system.  If you need it for normal maintenance, it is probably included already.

While my 2011 article is a little dated, here's what I thought an Ubuntu Desktop needs for maintenance: [https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282](https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282)
No extra tools that aren't already installed used.  I updated it in 2021: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

BTW, you stopped the ping using <cntl>-z, that didn't kill the process.  <cntl>-c does that, so you have a job running until the system is rebooted.  Using job control is a basic skill in Linux.  I'd use **fg %3** to make that background job come to the foreground, then then cntl-c it.  Most beginning Unix texts have job control in the chapter about shells.

---

### Post by deadflowr on 2023-11-13
> **ian-weisser said:**
> ports.ubuntu.com does not have amd64
Use a different mirror for that architecture.

Agreed.
ports.ubuntu does not have any amd64 packages, so...

> I also get a bunch of errors saying that certain repositions are listed in sources.list multiple times. (That isn't true, however. Each repository is listed twice, but once as an amd64 repository and once as an arm64 repository. The specific lines that is refers to as replicative are the proposed release repositories, whereas the first are the stable repositories. So, I'm not sure where this error comes from.) In either case, that wouldn't prevent Ubuntu from downloading the packages. Each repository gives an error 404.

We need to see the sources.list to know what you set or how it's set.

from the apt update output something is not right.

---

