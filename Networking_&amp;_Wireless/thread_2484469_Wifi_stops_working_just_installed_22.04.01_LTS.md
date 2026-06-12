---
title: "Wifi stops working just installed 22.04.01 LTS"
date: 2023-02-27
forum: Networking &amp; Wireless
---

### Post by daveyb415 on 2023-02-27
Install went fine the only issue is snap-store doesn't work, which I think may due to internet download slows to crawl.  Wireless-info output is at the pastebin link below - THx  (dell latitude e6410 / Intel® Core&#8482; i5 CPU M 520 @ 2.40GHz × 4 / 4.0 Gb RAM / 300 Gb on HD avail / Ubuntu 22.04.02 LTS fresh install) 

[https://pastebin.com/6H8txAKv#B62eDYaq](https://pastebin.com/6H8txAKv#B62eDYaq)

---

### Post by chili555 on 2023-02-27
Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

### Post by daveyb415 on 2023-02-28
Tried:  sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/* 
Retuned:sed couldn't edit /etc/NetworkManager/conf.d: not a regular file


The next two
sudo iw reg get
sudo iw reg set IS
Returned: iw: command not found


sudo nano /etc/default/crda
This opened the nano window but there was no line to edit. Just a blank screen with the nano menu across the bottom of the Terminal window.  None of the commands did anything GNU nano 6.2 window was blank and the none of the commands resulted in any action. Tried ^X for exit, ^G for help, M-U for undo, nothing happened.

It is strange.

---

### Post by mIk3_08 on 2023-02-28
> **daveyb415 said:**
> 
[https://pastebin.com/6H8txAKv#B62eDYaq](https://pastebin.com/6H8txAKv#B62eDYaq)
I prefer Ubuntu pastebin so I don't need to register at this site just to see the info you post here. By the way, I also experience this issue but I manage to solve it right a way. Regards and cheers.

---

### Post by chili555 on 2023-02-28
> Tried: sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
Retuned:sed couldn't edit /etc/NetworkManager/conf.d: not a regular filePlease double-check your command and try again. Your paste shows that it's there:
> [[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

I suspect that the changes in your router will yield better results. Please try those and when your speed is improved, run:

```
sudo apt update
sudo apt -install -y iw wireless-regdb
```Then try the iw commands again.

---

### Post by daveyb415 on 2023-02-28
Tried again: [COLOR=#000000] sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*[/COLOR]

Returned:
  Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
      --debug
                 annotate program execution
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  --follow-symlinks
                 follow symlinks when processing in place
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if SUFFIX supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -E, -r, --regexp-extended
                 use extended regular expressions in the script
                 (for portability use POSIX -E).
  -s, --separate
                 consider files as separate rather than as a single,
                 continuous long stream.
      --sandbox
                 operate in sandbox mode (disable e/r/w commands).
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
  -z, --null-data
                 separate lines by NUL characters
      --help     display this help and exit
      --version  output version information and exit


If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.


GNU sed home page: <https://www.gnu.org/software/sed/>.
General help using GNU software: <https://www.gnu.org/gethelp/>

sudo apt update
ran fine. said I had somethings that could be upgraded so I requested the list and it returned

rn3ss@rn3ss-Latitude-E6410:~$ apt list --upgradable
Listing... Done
isc-dhcp-client/jammy-updates 4.4.1-2.3ubuntu2.4 amd64 [upgradable from: 4.4.1-2.3ubuntu2.3]
isc-dhcp-common/jammy-updates 4.4.1-2.3ubuntu2.4 amd64 [upgradable from: 4.4.1-2.3ubuntu2.3]
libgnutls30/jammy-updates,jammy-security 3.7.3-4ubuntu1.2 amd64 [upgradable from: 3.7.3-4ubuntu1.1]
python3-macaroonbakery/jammy-updates,jammy-updates 1.3.1-2ubuntu0.1 all [upgradable from: 1.3.1-2]
tar/jammy-security 1.34+dfsg-1ubuntu0.1.22.04.1 amd64 [upgradable from: 1.34+dfsg-1build3]

Ran:
n3ss@rn3ss-Latitude-E6410:~$ sudo apt -install -y iw wireless-regdb

E: Command line option 'i' [from -install] is not understood in combination with the other options.

Tried IWs again:

rn3ss@rn3ss-Latitude-E6410:~$ sudo iw reg get
sudo: iw: command not found

rn3ss@rn3ss-Latitude-E6410:~$ sudo iw reg IS
sudo: iw: command not found

I think it is my network card, it  keeps shutting down or not starting.  THx for the suggestions.

---

### Post by chili555 on 2023-02-28
> Tried again: sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*

Returned:
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

-n, --quiet, --silent
suppress automatic printing of pattern spaceI don't know what to suggest. Did you copy and paste the command above? I did and got this:

```
chili@T440p:~$ sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
[sudo] password for chili: 
chili@T440p:~$ 
```

When I check to see what is in the file, I get:

```
chili@T440p:~$ cat /etc/NetworkManager/conf.d/*
[connection]
wifi.powersave = 2
chili@T440p:~$ 

```That is, the 3 has been replaced in place with a 2, as expected.

> n3ss@rn3ss-Latitude-E6410:~$ sudo apt -install -y iw wireless-regdb

E: Command line option 'i' [from -install] is not understood in combination with the other options.
That is my mistake and I apologize. Sorry. I meant to do:

```
sudo apt install -y iw wireless-regdb

```Please try again.

---

### Post by chili555 on 2023-02-28
In your sed command, did you type `, the backtick on the same key with ~? Or did you, as preferred, type the apostrophy ' on the same key with "? You want the apostrophy. Even better, as I suggest, copy and paste from my post #2.

---

### Post by rn3ss66 on 2023-03-01
Thx will follow suggestions, I am away from the machine until Thursday, appreciate the help. Will be back.

---

### Post by daveyb415 on 2023-03-05
Sorry I was not around machine for a few days. 
I did rerun:  [COLOR=#000000][FONT=&quot]sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/* by using C&P
[/FONT][/COLOR]I was prompted for  my pw, I checked and to confirm wifi powersave = 2.  

Then I reran: [COLOR=#000000][FONT=&quot]sudo apt install -y iw wireless-regdb
[/FONT][/COLOR]output
rn3ss@rn3ss-Latitude-E6410:~$ sudo apt install -y iw wireless-regdb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
wireless-regdb is already the newest version (2022.06.06-0ubuntu1~22.04.1).
wireless-regdb set to manually installed.
The following NEW packages will be installed:
  iw
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 108 kB of archives.
After this operation, 305 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 iw amd64 5.16-1build1 [108 kB]
Fetched 108 kB in 1s (212 kB/s)
Selecting previously unselected package iw.
(Reading database ... 197708 files and directories currently installed.)
Preparing to unpack .../iw_5.16-1build1_amd64.deb ...
Unpacking iw (5.16-1build1) ...
Setting up iw (5.16-1build1) ...
Processing triggers for man-db (2.10.2-1) ...

I then reattempted: sudo iw reg get
Output
global
country US: DFS-FCC
	(902 - 904 @ 2), (N/A, 30), (N/A)
	(904 - 920 @ 16), (N/A, 30), (N/A)
	(920 - 928 @ 8), (N/A, 30), (N/A)
	(2400 - 2472 @ 40), (N/A, 30), (N/A)
	(5150 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5350 @ 80), (N/A, 24), (0 ms), DFS, AUTO-BW
	(5470 - 5730 @ 160), (N/A, 24), (0 ms), DFS
	(5730 - 5850 @ 80), (N/A, 30), (N/A), AUTO-BW
	(5850 - 5895 @ 40), (N/A, 27), (N/A), NO-OUTDOOR, AUTO-BW, PASSIVE-SCAN
	(5925 - 7125 @ 320), (N/A, 12), (N/A), NO-OUTDOOR, PASSIVE-SCAN
	(57240 - 71000 @ 2160), (N/A, 40), (N/A)

My county code is correct.  Hope I did get this right this time - TY

---

### Post by chili555 on 2023-03-05
Excellent!

Now were you able to address the router settings that I recommended in post #2? I suspect that they will have the greatest effect.

---

### Post by daveyb415 on 2023-03-05
Sorry - forgot to comment regarding router. It isn't my router, it is landlords. He confirmed that it is not a mix of WPA & WPA2. He said that it is set for auto B, G, and N.  The router works great on my other devices.   
Thx

---

### Post by chili555 on 2023-03-05
> The router works great on my other devices.I have no doubt; however, the combination of Network Manager and a great many Linux wireless drivers does not in this scenario.

You might try binding to the 5 gHz segment like this: [https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112](https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112) A scan will show that they have different MAC addresses:

```
sudo iwlist scan
```

---

### Post by daveyb415 on 2023-03-06
Ran the scan and followed the question you linked to, the address was already in the drop down menu, I just selected the address that was in the scan.
BC:64:4B:OF:7F:BD. 

I am going to see what difference this makes. I will track the performance for the rest of the evening. THx.

---

### Post by daveyb415 on 2023-03-06
The internet is running consistently.  I would call this resolved. Thank you so much for all the assistance.  This forum is amazing!

---

### Post by mIk3_08 on 2023-03-07
> **daveyb415 said:**
> The internet is running consistently.  I would call this resolved. Thank you so much for all the assistance.  This forum is amazing!

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

