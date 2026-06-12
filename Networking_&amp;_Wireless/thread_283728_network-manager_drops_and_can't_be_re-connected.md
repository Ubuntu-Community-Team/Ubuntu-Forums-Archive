---
title: "network-manager drops and can't be re-connected"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by swiftsam on 2006-10-24
Hi,I'm a month into my ubuntu experience and loving it, thanks for all the good info I've gleaned from these forums as a lurker.  I haven't been able to find anything about my current problem though...

My set-up:
dell e1505 laptop
wpa wireless network
network-manager-gnome

My wireless worked out-of-box once I installed network-manager-gnome and added the network passkey to the keyring. 

The problem is that a couple of times per day the connection will drop out.  I have another computer also on the wireless right next to it, so I'm sure that has to do with the laptop.  The icon will change to 'No Network Connection' and all the options will suddenly be gone from the list of networks to connect to.  If i reboot, it will work fine again immeditately after.

As a stop-gap solution, I would love to know what command to use in terminal to restart the network-manager so that I don't have to reboot.

Beyond that, any actual solutions or links to related threads that I couldn't find would be great.

Thanks very much

edit: this seems very similar to the problem in this thread [http://ubuntuforums.org/showthread.php?t=282443](http://ubuntuforums.org/showthread.php?t=282443)
which hit the top of the forum 1 minute before i posted. hehe

what terminal command can I use to get an actual error message?

---

### Post by swiftsam on 2006-10-24
in an effort to provide more info i ran iwconfig as I saw in the related thread I linked to above

```
samswift@smueltogo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8256   Missed beacon:0

sit0      no wireless extensions.
```

not sure why my wireless connection is called eth1 instead of wlan0 as seems to be most people's set-up.  could that be part of the problem?

again, i would be plenty satisfied with a command to refresh/restart my wireless just to save me the reboot

---

### Post by swiftsam on 2006-10-25
For anyone that has a similiar problem, this seemed to work for me, at least to restart things

```
sudo /etc/init.d/networking restart
```

after doing that, I see choices again in my network manager list and I successfully connected.  So, I'll keep my eyes peeled for a real solution, but at least this lets me continue working.

---

### Post by swiftsam on 2006-10-25
ah damn, it doesn't work consistently.  When I first used my computer this morning, the network was out, and that seemed to fix it.  But just now, it fell back into the 'No Network Connection' rut, and the '/etc/init.d/networking restart' doesn't seem to be doing anything.  It says [ok], but nothing changes.

anybody have any other tips on how to restart everything to do with networking so that I don't have to reboot?

---

### Post by swiftsam on 2006-10-25
I thought it might help to post a couple other diagnostic ouputs I've seen the experts ask for on other people's threads

```
samswift@smueltogo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:25:33:0F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

eth1      Link encap:Ethernet  HWaddr 00:13:02:B8:3D:BF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:33 dropped:1597 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1672608 (1.5 MiB)  TX bytes:25692126 (24.5 MiB)
          Interrupt:169 Base address:0xc000 Memory:dfcff000-dfcfffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8720 (8.5 KiB)  TX bytes:8720 (8.5 KiB)
```

If I run iwlist while I'm having connection problems i get this
```
samswift@smueltogo:~$ iwlist scan
lo        Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
```

but after a reboot I get this again
```
samswift@smueltogo:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:31:08:BD
                    ESSID:"5411"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=73/100  Signal level=-61 dBm  Noise level=-61 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 100ms ago

sit0      Interface doesn't support scanning.
```

anything else I could run to add clues?

---

### Post by swiftsam on 2006-10-25
one more thing, and I promise I'll stop pestering the board until somebody replies...

my /etc/network/interfaces  looks like this
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

I honestly can't remember now, but I think I commented out all those lines while setting up network-manager upon recommendation from somewhere on this forum.  Does that look like a good set-up?

---

### Post by yargevad on 2006-11-06
I'm getting the AP:Not-Associated errors too. It happens when the wireless signal I'm connected to goes below a certain point and appears to be unrecoverable except for rebooting, just like you said yours was. Looks like your signal is fine though - or is it fluctuating? Here's a little script to monitor the quality of the various networks you can see:```
#!/usr/bin/perl
use strict;

use Getopt::Long;
#use Time::HiRes 'time';

my $iface = 'ath0'; # name of the interface to query
my $freq  = 1;      # pause between queries, in seconds
my $usage = 0;
my $rv = GetOptions(
  'interface=s' => \$iface,
  'frequency=i' => \$freq,
  'help'        => \$usage,
);
usage() && exit if not $rv or $usage;
sub usage {
  print <<USAGE;
$0 [--interface ath0] [--frequency 0.5] [--help]
  interface - query an interface other than the default ath0
  frequency - query the interface at a frequency other than every second
  help - print this message
USAGE
}

my $input;
while (1) {
  my $iwlist = `iwlist $iface scan`;
  my @cells = split /^\s+Cell \d+/m, $iwlist;
  my $printme = '';
  for my $cell (@cells) {
    my ($ssid) = $cell =~ /ESSID:"([^"]*)"/;
    next if not $ssid;
    my ($quality, $max) = $cell =~ /Quality=(\d+)\/(\d+)/;
    my ($encrypted) = $cell =~ /Encryption key:(\w+)/;
    $printme .= "$ssid: ". ($encrypted eq 'off' ? 'not ' : '') ."encrypted, $quality/$max\n|";
    $printme .= '*' x $quality;
    $printme .= '-' x ($max-$quality);
    $printme .= "|\n";
    # i don't know how to make this (appear to) seamlessly update any other way
    print "\n" x 50; 
    print $printme;
  }
  #(my $ms = time) =~ s/^\d+\.//;
  #print "sleeping $freq seconds: 0.$ms\n";
  select undef, undef, undef, $freq;
}

```
I have it saved as /sbin/iwsummary and run it as ```
sudo iwsummary
``` because otherwise (if iwlist is not run as root) it just queries old results instead of actually scanning.

---

