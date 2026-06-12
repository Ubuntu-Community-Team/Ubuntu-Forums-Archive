---
title: "Sharing and Advertising Ubuntu with Avahi and Netatalk"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by childofdust on 2007-01-26
This might already exist somewhere, or in numerous pieces on the forum, but I thought I would write up a brief explanation of how to get your Ubuntu box sharing home folders with your Mac OS X box.  I decided to use the native networking protocol AFP (over tcp) and advertise using zeroconf so I had a more seamless networking environment.  I use Ubuntu as a simple server and would like to access my home directory from time to time.  While I did find all of the pieces to do this between here, other forums, and a wiki, I thought it would be nice to have a simple all in one post that covered it all.  Pardon me if there is already something like it.  My installation of Ubuntu is Edgy running 2.6.17-10-powerpc (running on a mac mini).  I would assume that you could do the very same on the x86 version as well.  If someone reads this and has luck with it, please let me know. :)

First things first, in order to get AFP working, you'll need to install netatalk.  Now, the problem here is that netatalk as stored in the repositories does not have the proper plugin to facilitate encrypted passwords, so on the Mac side of things it will nag you about sending passwords in the clear.  We'll get by that pretty easily though by building the package ourselves.  Also, you need to make sure that you have the universe repositories available for the distribution.  Hop into the command line and from your home directory enter these commands:

```

sudo apt-get build-dep netatalk
sudo apt-get install cracklib2-dev fakeroot libssl-dev
sudo apt-get source netatalk
cd netatalk-2.0.3/
sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot
sudo dpkg -i ~/netatalk_2.0.3-4_i386.deb

```

Now that we have it installed, we want to make sure that dpkg does not overwrite our changes, so we run the command:
```
echo "netatalk hold" | sudo dpkg --set-selections
```

Netatalk should be installed, so we just need to share out the home directories.
```
nano /etc/netatalk/afpd.conf
```

Type this line into the file and save:
```
- -noddp -uamlist uams_randnum.so,uams_dhx.so
```

Now we need to create the file that directs netatalk to what we want shared.
```
nano /etc/netatalk/AppleVolumes.default
```

Type this into the file and save.  This shares each users home directory
```
~
```

Now just restarts the daemon and all is well.
```
sudo /etc/init.d/netatalk restart
```

All of this is well and good, but what if we want to make this more seamless we need to advertise the shared directory so that we can see it in Finder.  To do this, I decided to use Avahi so I could keep everything close to the way OS X does things with zeroconf.  First we install the daemon:

```
sudo apt-get install avahi-daemon
```

That's really all you need to do to get things up and running, but maybe you're like me and want to be able to ping in both directions.  If so, what you need to do is install a library to enable mDNS.  These next few steps are optional, but useful if you plan on mounting shares on the Ubuntu side of things.
```
sudo apt-get install libnss-mdns
```

Also, we need to add mdns as a valid means for host lookup.
```
sudo nano /etc/nsswitch.conf
```

find the line with label "hosts:" (probably line 12) and add mdns to the end so that it reads:
```
hosts:[INDENT]files dns mdns[/INDENT]
```

Now that we have avahi working both ways and set up correctly, we need to advertise that we are running an AFP service on our machine.  To do that:
```
sudo nano /etc/avahi/services/afpd.service
```

Now just paste / type out what you see below:
```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_afpovertcp._tcp</type>
    <port>548</port>
  </service>

</service-group>
```

Save the file and then restart the avahi daemon.
```
sudo /etc/init.d/avahi-daemon restart
```

When your network catches up to you, and it might take a few minutes, you should see your newly shared out home directories in the Mac OS X finder.  The last thing we need to do is load avahi at boot.  To do this, just:
```
sudo nano /etc/default/avahi-daemon
```

and change
```
AVAHI_DAEMON_START=0 to AVAHI_DAEMON_START=1
```

If you run into problems setting up Avahi, you can always go to:
[Ubuntu Wiki on Zeroconf]("https://help.ubuntu.com/community/HowToZeroconf")  Hope this helps out someone!  I apologize for my ridiculous use of the code tag.

---

### Post by MaXqUE on 2007-02-12
hello:

LIne 6 in the first code window should be:

```
 DEB_BUILD_OPTIONS=ssl sudo dpkg-buildpackage -rfakeroot
```

dpkg-buildpackage will fail without a sudo in that line.

Thanks for posting this though, it is a life save!

Cheers,
MaXqUE

---

### Post by MaXqUE on 2007-02-13
Hello:

There seems to be a problem with the gpg keys for this code. This is the last lines of the netatlk compile .. looks like it failed trying to confirm the signature:

```
 dh_strip -pnetatalk  
dh_compress -pnetatalk  
dh_fixperms -pnetatalk  
dh_makeshlibs -pnetatalk  
dh_installdeb -pnetatalk 
dh_perl -pnetatalk 
dh_shlibdeps -pnetatalk    
dh_gencontrol -pnetatalk -- -Vssl:Recommends=", cracklib-runtime, libpam-cracklib"
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums -pnetatalk 
dh_builddeb -pnetatalk 
dpkg-deb: building package `netatalk' in `../netatalk_2.0.3-4_i386.deb'.
tar: -: file name read contains nul character
 signfile netatalk_2.0.3-4.dsc
gpg: keyring `/home/katatak/.gnupg/secring.gpg' created
gpg: skipped "Sebastian Rittau <srittau@debian.org>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
(WARNING: Failed to sign .dsc and .changes file)

```

grrrr .. more gpg signature problems!

Cheers,
MaXqUE

---

### Post by rbarrimond on 2007-03-06
Thank You!

Just a quick update.  To publish the afpd service your path and file name were incorrect.  It should be:
```
sudo nano /etc/avahi/services/afpd.service
```
Once I made that change.  Everything went peachy!

---

### Post by helbro on 2008-04-01
Hi kids...

I am successfully running Netatalk (on Ubuntu 8.04 Hardy Heron) with MacOSX 10.5 Leopard

I had some problems setting it up (Netatalk, avahi-daemon, and mdns). I have finally figured out all that needs to be done, and I thought I'd share it with you guys in the hopes of saving someone else the work of figuring out.

I should say that I am not even sure if other people have the same difficulties I had, but for what it's worth:

It is my understandning that Netatalk 2.0.3-7 (in the Hardy repos) are non-functional. There is a fix .diff you could apply, though I chose to run th the newer (though experimental) version: 2.0.3-8.

These following steps are very similar to the original posters, this is not verbose, and it doesnt have to be. copy - paste...
```

mkdir -p ~/src/netatalk
cd ~/src/netatalk
sudo aptitude install devscripts cracklib2-dev dpkg-dev libssl-dev build-essential
sudo apt-get build-dep netatalk
wget http://ftp.de.debian.org/debian/pool/main/n/netatalk/netatalk_2.0.3.orig.tar.gz
wget http://ftp.de.debian.org/debian/pool/main/n/netatalk/netatalk_2.0.3-8.diff.gz 
wget http://ftp.de.debian.org/debian/pool/main/n/netatalk/netatalk_2.0.3-8.dsc
dpkg-source -x ./netatalk_2.0.3-8.dsc
cd netatalk-2.0.3
sudo su
DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -us -uc
debi
exit
echo "netatalk hold" | sudo dpkg --set-selections
echo userpassword > ~/.passwd
chmod 600 ~/.passwd

```

Ok, at this point, you have downloaded, built netatalk (with ssl-support) , and installed it onto your system. Thats fine. 

now you have to tweak / att a few files:

fix /ets/netatalk/afpd.conf
```
sudo vim /etc/netatalk/afpd.conf
```
Add this at the bottom:
```
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword
```

OPTIONAL: If you are like me, and you want to share files only (not time server, printer servers and so on). This will speed up the starting and restarting of the services a lot! Edit:  /etc/default/netatalk 
```
sudo vim /etc/default/netatalk
```

Change this:
```

ATALKD_RUN=yes
PAPD_RUN=yes
CNID_METAD_RUN=no
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no

```

to this:
```

ATALKD_RUN=no
PAPD_RUN=no
CNID_METAD_RUN=no
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no

```

restart netatalk:
```
sudo /etc/init.d/netatalk restart
```

Install and conf avahi-daemon (with mdns). Again. This is very similar to the original poster. Refer to the first post of this thread for a more verbose instruction:
```

sudo apt-get install --reinstall avahi-daemon; sudo dpkg-reconfigure avahi-daemon
sudo apt-get install --reinstall libnss-mdns; sudo dpkg-reconfigure libnss-mdns

```

edit /ets/nsswitch.conf
```
sudo vim /etc/nsswitch.conf
```

At the end of the line that starts with "hosts:" add mdns. Mine reads:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 mdns
```

Add the file /etc/avahi/services/afpd.service:
```
sudo vim /etc/avahi/services/afpd.service
```

paste this in it:
```

<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_afpovertcp._tcp</type>
    <port>548</port>
  </service>

</service-group>

```

OPTIONAL: If you want to be able do Screen Sharing from clicking in the Finder side-bar, do this:
```

vino-preferences 

```

Modify the preferences:

Under General:
```

Check: "Allow other users to view your desktop"
Check: "Allow other users to control your desktop"
Uncheck: "Ask for your confirmation"
Check: "Require the user to enter this password" --> Preferably the same password as your users login-password.

```

Under Advanced: 
```

Uncheck: "Only local connections"
Check: "Use an alternate port:" Enter 5901
Uncheck: "Require Encryption" (I havent gotten this to work with Leopard)
Uncheck: "Lock screen on disconnect"
Choose: Only Display an icon when there is someone connected

```
Close the dialog box to save the settings.


Add the avahi service file:
```
sudo vim /etc/avahi/services/rfb.service
```

Paste this into the empty file: 
```

<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_rfb._tcp</type>
    <port>5901</port>
  </service>

</service-group>

```

Make sure the avahi daemon starts on system restart:
```
sudo nano /etc/default/avahi-daemon
```

make sure it says:
```
AVAHI_DAEMON_START=1
```

Restart avahi-daemon:
```
sudo /etc/init.d/avahi-daemon restart
```

Now everything should be working. Although, this is where it started to become a little weird for me. I found the linux-server in my Finder side-bar under "Shared". However, instead of just showing the services that we set up ourselves, it is also showing one that says the IP address of the server (which is ugly and disgusting), and one that says "[user]'s remote desktop on [host]" in my case: "nicke's remote desktop on hank". It took me a while to figure out how to get rid of these two while leaving the ones we defined intact: 

Here is how:

edit /etc/avahi/avahi-daemon.conf:
```
sudo vim /etc/avahi/avahi-daemon.conf
```

change 
```
#enable-dbus=yes
```
to:
```
enable-dbus=no
```
*Please note that you are not only changing "yes" to "no", you are also uncommenting the line to make it active.

That is about it. Now just restart both Netatalk and avahi-daemon to make sure that they read in all the new config files:

```
sudo /etc/init.d/netatalk restart; sudo /etc/init.d/avahi-daemon restart
```

You should be good to go.

Hope this helped someone.

Here are some screen shots to show yout what I mean by the "IP address" showing up. 

cheers .n

---

### Post by Eiríkr on 2008-04-01
For those looking to share via NFS instead of AFP, but still want that zeroconf automagic goodness, have a look at [post=4387032]this post over here[/post].

Cheers,

Eiríkr

---

### Post by Auryn on 2008-04-03
I encountered the same problem as helbro when setting up a Netatalk server with Hardy on my LAN last night.  The Finder on my Macs would show a share entry for both the server name and the server IP address.  I figured out the problem was that Netatalk has been patched to automatically register itself with Avahi, resulting in the automatic entry as well at the manual entry entered into /etc/avahi/services.

For some reason the automatic Avahi entry uses the IP address label instead of the hostname.  Since the manual entry works better, I just had to add ```
-nozeroconf
``` to the options given in /etc/netatalk/afpd.conf rather than switching off DBUS completely in the Avahi config.


I also couldn't be bothered compiling a new version of Netatalk with encryption built in since I'm only using AFP on my home LAN, so I just installed the latest Debian 2.0.3-8 package instead which seems to work fine on Hardy and fixes the bug in the current package that helbro mentioned.

I did discover though that Leopard now disables unencrypted AFP connections by default.  I fixed this with the help of [http://www.macosxhints.com/article.php?story=20071028025409750](http://www.macosxhints.com/article.php?story=20071028025409750) by entering ```
$ defaults write com.apple.AppleShareClient "afp_cleartext_allow" -bool YES
$ defaults write com.apple.AppleShareClient "afp_cleartext_warn" -bool YES
``` from the terminal and everything seems to work fine now.  I don't get cleartext warnings from Leopard even with the option set though for some reason.

---

### Post by supermac on 2008-04-06
Hi!

[QUOTE=childofdust;2067696]
```

sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot

```

Only gives me this:
```

~/netatalk-2.0.3$ sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot
sudo: DEB_BUILD_OPTIONS=ssl: command not found

```

Anyone know the solution to this?


Nevermind, solved it!

---

### Post by helbro on 2008-04-06
> **Auryn said:**
> I encountered the same problem as helbro when setting up a Netatalk server with Hardy on my LAN last night.  The Finder on my Macs would show a share entry for both the server name and the server IP address.  I figured out the problem was that Netatalk has been patched to automatically register itself with Avahi, resulting in the automatic entry as well at the manual entry entered into /etc/avahi/services.

For some reason the automatic Avahi entry uses the IP address label instead of the hostname.  Since the manual entry works better, I just had to add ```
-nozeroconf
``` to the options given in /etc/netatalk/afpd.conf rather than switching off DBUS completely in the Avahi config.



@Auryn: I tried your suggestion to put -nozeroconf, and it does remove the IP-address entry, however I am left with the ones i appointed myself + one that says: "my screensharing on hank."

If someone doesn't have a way to remove this without disabling dbus, Im left with no choice..

what does dbus do anyway? I haven't really noticed any lack of functionality without it...

sincerely, 

Niclas

---

### Post by FoolsRun on 2008-04-15
Disabling dbus stops services from registering themselves with Avahi. Services like CUPS, which I'm using to share my printers.

As such, disabling dbus is not an option for me, however adding -nozeroconf to afpd.conf does not remove the IP address entry from my Finder.

Could this have to do with the manual compile of netatalk? I'm at a loss for why my finder still shows both the hostname and the IP address as separate entries.

---

### Post by the ev on 2008-05-13
Simply awesome; exactly what I was looking for.  You've made the world a better place, childofdust, starting with my home network.  :)

---

### Post by kapetanski on 2008-07-10
After running sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot I get this output (starting at the first error):


```
make[1]: *** No rule to make target `distclean'.
make[1]: Leaving directory `/home/beta/netatalk-2.0.3'
make: [makefile-clean] Error 2 (ignored)
rm -f debian/stamp-makefile-build
rm -f debian/stamp-autotools-files
/usr/bin/make -f debian/rules reverse-config
make[1]: Entering directory `/home/beta/netatalk-2.0.3'
for i in ./config.guess ./config.sub  ; do \
		if test -e $i.cdbs-orig ; then \
			mv $i.cdbs-orig $i ; \
		fi ; \
	done
make[1]: Leaving directory `/home/beta/netatalk-2.0.3'
if [ -d "." ] ; then \
	  cd . && QUILT_PATCHES=patches quilt --quiltrc /dev/null pop -a -R || test $? = 2 ; \
	fi 
No patch removed
if [ -n "patches" ] ; then \
	  if [ -L ./patches ] ; then \
	    rm ./patches ; \
	  fi ; \
	fi
rm -rf ./.pc
rm -f debian/stamp-patch*
rm -f debian/stamp-buildinfo
rm -f debian/stamp-copyright-check
rm -f AUTHORS ChangeLog INSTALL
rm -rf m4
rm -f debian/netatalk.init
 dpkg-source -b netatalk-2.0.3
dpkg-source: building netatalk using existing netatalk_2.0.3.orig.tar.gz
dpkg-source: building netatalk in netatalk_2.0.3-9.diff.gz
dpkg-source: building netatalk in netatalk_2.0.3-9.dsc
 debian/rules build
test -x debian/rules
mkdir -p "."
Scanning upstream source for new/changed copyright notices (except debian subdir!)...
licensecheck -c '.*' -r --copyright -i '^(debian/.*|(.*/)?config\.(guess|sub|rpath)(\..*)?)' * \
		| LC_ALL=C perl -e \
	'$n=0; while (<>) {'\
	'	if (/^([^:\s][^:]+):[\s]+(\S.*?)\s*$/) {'\
	'		$files[$n]{name}=$1;'\
	'		$files[$n]{license}=$2;'\
	'	};'\
	'	if (/^\s*\[Copyright:\s*(\S.*?)\s*\]/) {'\
	'		$files[$n]{copyright}=$1;'\
	'	};'\
	'	/^$/ and $n++;'\
	'};'\
	'foreach $file (@files) {'\
	'	$file->{license} =~ s/\s*\(with incorrect FSF address\)//;'\
	'	$file->{license} =~ s/\s+\(v([^)]+) or later\)/-$1+/;'\
	'	$file->{copyright} =~ s/(?<=(\b\d{4}))(?{$y=$^N})\s*[,-]\s*((??{$y+1}))\b/-$2/g;'\
	'	$file->{copyright} =~ s/(?<=\b\d{4})\s*-\s*\d{4}(?=\s*-\s*(\d{4})\b)//g;'\
	'	$pattern = "$file->{license} [$file->{copyright}]";'\
	'	push @{ $patternfiles{"$pattern"} }, $file->{name};'\
	'};'\
	'foreach $pattern ( sort {'\
	'			@{$patternfiles{$b}} <=> @{$patternfiles{$a}}'\
	'			||'\
	'			$a cmp $b'\
	'		} keys %patternfiles ) {'\
	'	print "$pattern: ", join("\n\t", sort @{ $patternfiles{$pattern} }), "\n";'\
	'};'\
		> debian/copyright_newhints
Found 736 different copyright and licensing combinations.
ERROR: The following new or changed copyright notices discovered:

UNKNOWN [1998 Owen Taylor</p><p>Permission to use, copy, modify, and distribute this software and / notice appear in all copies and that / notice and this permission notice appear in supporting]: doc/htmldocs/netatalkconfig.1.html

To fix the situation please do the following:
  1) Investigate the above changes and update debian/copyright as needed
  2) Replace debian/copyright_hints with debian/copyright_newhints
make: *** [debian/stamp-copyright-check] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

```

I don't know what to do :(

---

### Post by mikcomf on 2008-07-15
you need to rename the file copyright_newhints to copyright_hints:

$sudo mv copyright_hints copyright_hints~
$sudo mv copyright_newhints copyright_hints

then try again.

---

