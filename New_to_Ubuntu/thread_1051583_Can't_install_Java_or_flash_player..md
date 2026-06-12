---
title: "Can't install Java or flash player."
date: 2009-01-26
forum: New to Ubuntu
---

### Post by psychobilly freakout on 2009-01-26
I've been trying to install both these features and it does not work.
For Java i get this error message:Could not display desktop/jre-6ull-linux-x64.bin (there is no application installed for this type).

And for the flash player i only get read me files and thats it.

---

### Post by LostMagix on 2009-01-26
What method are you using to install them?

---

### Post by Crafty Kisses on 2009-01-26
You could always install this package:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by psychobilly freakout on 2009-01-26
> **Codename said:**
> You could always install this package:
```
sudo apt-get install ubuntu-restricted-extras
```

When i copy it in i get this :

E: Couldn't find package ubuntu-restricted-extras

---

### Post by Crafty Kisses on 2009-01-26
What version of Ubuntu are you using? Try the following and see if you get different results:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by psychobilly freakout on 2009-01-26
> **Codename said:**
> What version of Ubuntu are you using? Try the following and see if you get different results:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Ok when i enter either of them i get this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

And as far as i know im currently using version 8.10

---

### Post by perlluver on 2009-01-26
> **psychobilly freakout said:**
> Ok when i enter either of them i get this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

And as far as i know im currently using version 8.10

Do you have Synaptic or Add/Remove programs open?

---

### Post by Crafty Kisses on 2009-01-26
Make sure you don't have another instance of Synaptic running.

---

### Post by LostMagix on 2009-01-26
Do you have any other Synpatic programs open (Synpatic Package Magager, Add/Remove)

---

### Post by psychobilly freakout on 2009-01-26
Nope

---

### Post by Crafty Kisses on 2009-01-26
Post the results of this command:
```
ps -A
```

---

### Post by psychobilly freakout on 2009-01-26
> **Codename said:**
> Post the results of this command:
```
ps -A
```

Results:

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  130 ?        00:00:00 cqueue
  134 ?        00:00:00 kseriod
  177 ?        00:00:00 pdflush
  178 ?        00:00:00 pdflush
  179 ?        00:00:01 kswapd0
  219 ?        00:00:00 aio/0
  220 ?        00:00:00 aio/1
 1161 ?        00:00:00 ksuspend_usbd
 1162 ?        00:00:00 khubd
 1222 ?        00:00:00 ata/0
 1225 ?        00:00:00 ata/1
 1229 ?        00:00:00 ata_aux
 1230 ?        00:00:00 khpsbpkt
 1936 ?        00:00:00 knodemgrd_0
 1937 ?        00:00:00 scsi_eh_0
 1938 ?        00:00:00 scsi_eh_1
 2082 ?        00:00:37 mount.ntfs
 2121 ?        00:00:09 loop0
 2123 ?        00:00:01 kjournald
 2300 ?        00:00:00 udevd
 2527 ?        00:00:00 pccardd
 2532 ?        00:00:00 kmmcd
 2568 ?        00:00:00 kpsmoused
 4548 tty4     00:00:00 getty
 4549 tty5     00:00:00 getty
 4552 tty2     00:00:00 getty
 4553 tty3     00:00:00 getty
 4554 tty6     00:00:00 getty
 4741 ?        00:00:00 acpid
 4772 ?        00:00:01 kondemand/0
 4774 ?        00:00:00 kondemand/1
 4866 ?        00:00:00 syslogd
 4916 ?        00:00:00 dd
 4918 ?        00:00:00 klogd
 4941 ?        00:00:01 dbus-daemon
 4963 ?        00:00:00 avahi-daemon
 4964 ?        00:00:00 avahi-daemon
 5010 ?        00:00:00 cupsd
 5069 ?        00:00:00 hald
 5072 ?        00:00:00 console-kit-dae
 5073 ?        00:00:00 hald-runner
 5156 ?        00:00:00 hald-addon-inpu
 5166 ?        00:00:00 hald-addon-cpuf
 5167 ?        00:00:00 hald-addon-acpi
 5173 ?        00:00:00 hald-addon-stor
 5217 ?        00:00:00 bluetoothd
 5223 ?        00:00:00 btaddconn
 5224 ?        00:00:00 btdelconn
 5250 ?        00:00:00 krfcommd
 5279 ?        00:00:00 NetworkManager
 5290 ?        00:00:00 wpa_supplicant
 5297 ?        00:00:00 nm-system-setti
 5317 ?        00:00:00 gdm
 5320 ?        00:00:00 gdm
 5323 tty7     00:08:01 Xorg
 5357 ?        00:00:00 system-tools-ba
 5392 ?        00:00:00 atd
 5420 ?        00:00:00 cron
 5519 tty1     00:00:00 getty
 5548 ?        00:00:00 gnome-keyring-d
 5559 ?        00:00:00 x-session-manag
 5649 ?        00:00:00 dbus-launch
 5650 ?        00:00:00 dbus-daemon
 5653 ?        00:00:00 pulseaudio
 5656 ?        00:00:00 gconf-helper
 5658 ?        00:00:03 gconfd-2
 5664 ?        00:00:00 seahorse-agent
 5669 ?        00:00:00 gnome-keyring-d
 5671 ?        00:00:03 gnome-settings-
 5673 ?        00:00:00 compiz
 5706 ?        00:00:00 gvfsd
 5739 ?        00:00:36 compiz.real
 5743 ?        00:00:00 gvfs-fuse-daemo
 5756 ?        00:00:10 gnome-screensav
 5760 ?        00:00:00 sh
 5761 ?        00:00:00 compiz-decorato
 5763 ?        00:00:13 gtk-window-deco
 5764 ?        00:00:21 gnome-panel
 5765 ?        00:00:03 nautilus
 5768 ?        00:00:00 bonobo-activati
 5778 ?        00:00:00 gvfs-hal-volume
 5780 ?        00:00:00 gvfs-gphoto2-vo
 5787 ?        00:00:00 trashapplet
 5789 ?        00:00:00 gvfsd-burn
 5791 ?        00:00:00 gvfsd-trash
 5807 ?        00:00:01 fast-user-switc
 5812 ?        00:00:00 mixer_applet2
 5822 ?        00:00:00 evolution-alarm
 5823 ?        00:00:01 trackerd
 5826 ?        00:00:00 python
 5831 ?        00:00:01 update-notifier
 5832 ?        00:00:00 tracker-applet
 5835 ?        00:00:02 nm-applet
 5838 ?        00:00:00 bluetooth-apple
 5839 ?        00:00:01 gnome-power-man
 5892 ?        00:00:02 notification-da
 5909 ?        00:00:00 dhclient
 6036 ?        00:05:54 firefox
 6726 ?        00:00:10 update-manager
 6771 ?        00:00:16 pidgin
 7019 ?        00:00:00 gksu
 7020 ?        00:00:07 synaptic
 7032 ?        00:00:00 http
 7106 ?        00:00:00 anacron
 7134 ?        00:00:00 gnome-terminal
 7137 ?        00:00:00 gnome-pty-helpe
 7138 pts/0    00:00:00 bash
 7156 pts/0    00:00:00 ps

---

### Post by Crafty Kisses on 2009-01-26
Looks like you have Synaptic running:
```
7020 ? 00:00:07 synaptic
```

---

### Post by psychobilly freakout on 2009-01-26
> **Codename said:**
> Looks like you have Synaptic running:
```
7020 ? 00:00:07 synaptic
```

Result:

bash: 7020: command not found

---

### Post by Crafty Kisses on 2009-01-26
You weren't supposed to even enter that as a command, I was just pointing out you have Synaptic running somewhere. You need to close Synaptic, then install the package I told you to install.

---

### Post by psychobilly freakout on 2009-01-26
> **Codename said:**
> You weren't supposed to even enter that as a command, I was just pointing out you have Synaptic running somewhere. You need to close Synaptic, then install the package I told you to install.

What is a synaptic? and how do i find it?

*Im still new to ubuntu.

---

### Post by perlluver on 2009-01-26
It should most likely be minimized on your bar, it also appears you have Update manager running.

---

### Post by Crafty Kisses on 2009-01-26
Ok so here do the following, enter the following command:
```
ps -A
```
Look for Synaptic in that list, there should be a process ID before the process name, so for example last time the process ID was 7020 for Synaptic, so it might be different now, so look through the list for Synaptic, once you find it, and the process ID, run the following command:
```
sudo kill 7020
```
I'm just assuming Synaptic's process ID is 7020, but you get the point.

---

### Post by igknighted on 2009-01-26
Regardless, you have 64bit Ubuntu installed.  The 64 bit flash plugin (or at least one that works) isn't in the repo's, so you don't need to worry about the package management system to install it.  Go to [http://labs.adobe.com](http://labs.adobe.com) to get flash player 10 for 64bit linux.

For java... this is slightly more complicated.  If you just need to run java programs on your computer, the package to install is 'sun-java6-jre', or 'sun-java6-jdk' if you want to program in java.  If you need the web browser plugin (for java applets online, for example), then you need the 64bit browser plugin.  It is only available in the very latest java package from sun, so if you need this post back for further instructions.

Oh... and I would strongly recommend that you do NOT install the 'ubuntu-restricted-extras' package.  This will install the 32bit java and flash plugins with a plugin wrapper that works really poorly.  If you want the plugins, get the 64bit versions, even though the install is harder.  It will make life much easier in the long run.

---

### Post by psychobilly freakout on 2009-01-26
Ok so synaptic was not there once i closed my update manager, so i was able to download some stuff but im still not able to download java i still get the same message as before.

---

### Post by igknighted on 2009-01-26
> **psychobilly freakout said:**
> Ok so synaptic was not there once i closed my update manager, so i was able to download some stuff but im still not able to download java i still get the same message as before.

What do you want java installed for... apps like frostwire, or applets online?

---

### Post by Crafty Kisses on 2009-01-26
So download the latest version from Java right here: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp). My instructions are going to assume you're going to save it to your desktop and the file name is "java.bin". So what you want to do is navigate to the Terminal and run these commands:
```
cd ~/Desktop
chmod +x java.bin
sudo mv java.bin /opt
cd /opt
sudo ./java.bin

```
Once you've done that it will start unzipping the files in the /opt directory, there should be a new directory, and not sure what it would be called, but navigate to it:
```
cd jre_directory/bin
sudo ln -s /opt/jre_directory/bin/java /usr/local/bin/java
```
There's also instructions on Java's website if you don't understand mine, but if you followed mine, that should get Java up and running.

---

### Post by psychobilly freakout on 2009-01-26
Ok when i try to install the flash player and when i try to extract it i keep getting these error messages

When i try to extract the files i get this message:
Could not open the file kmess-1.5.1.x86.package using the Western (ISO-8859-15) character coding.

or 

Could not open the file kmess-1.5.1.x86.package using the Unicode (UTF-8) character coding.

---

### Post by igknighted on 2009-01-26
> **Codename said:**
> So download the latest version from Java right here: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp). My instructions are going to assume you're going to save it to your desktop and the file name is "java.bin". So what you want to do is navigate to the Terminal and run these commands:
```
cd ~/Desktop
chmod +x java.bin
sudo mv java.bin /opt
cd /opt
sudo ./java.bin

```
Once you've done that it will start unzipping the files in the /opt directory, there should be a new directory, and not sure what it would be called, but navigate to it:
```
cd jre_directory/bin
sudo ln -s /opt/jre_directory/bin/java /usr/local/bin/java
```
There's also instructions on Java's website if you don't understand mine, but if you followed mine, that should get Java up and running.

Would strongly recommend this version (for 64bit plugin), not the default one java.com will give you: [http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin](http://www.java.net/download/jdk6/6u12/promoted/b03/binaries/jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin)

---

### Post by teknorah on 2009-01-26
> **psychobilly freakout said:**
> What is a synaptic? and how do i find it?

*Im still new to ubuntu.
Synaptic is the type of Package manager (software store) that Ubuntu uses.  It can be accessed several ways:
Menus: Applications>Add/Remove or System>Administration>Synaptic Package Mangager
Some other ways it may be open:  Update Manager via orange star icon on top bar near clock (or menu: System>Administration>Update Manager

As far as getting flash installed, the easiest way I do it every time, is I go to a website that has flash content (Ex: [hulu.com]("http://www.hulu.com")) and a bar appears at the top of the webpage w/ a button to install missing plugins.  I click on that, select Adobe/Flash (1st one on list), click install/yes/ok a few times, close and reopen firefox and go the website again: Voila! I have flash.
 -  EDIT: Didn't realize you were running 64-bit, prolly best to follow other suggestions on this thread for 64-bit

Some useful links regarding Ubuntu Package Management, Flash and Java:
[Synaptic]("https://help.ubuntu.com/community/SynapticHowto")
[Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash") (also [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") is a good read)
[Java]("https://help.ubuntu.com/community/Java")

In general, [Ubuntu Official Documentation Pages]("https://help.ubuntu.com/") are a good first step before jumping to the Forums for general questions.  But, please don't hesitate to post here, especially if you can't find the answer in on the Help pages.

---

### Post by psychobilly freakout on 2009-01-26
Ok

None of these downloads are not working properly, i am downloading the links that you guys are providing and when it's done i got to launch application and press ok and it goes onto the desktop.And when i try to open to file it says"could not display jre-6ul...3-linux-amd64-22_dec_2008.bin"
"the location is not a folder"

I've tried to download all other files from the java website and i keep getting the same thing.

---

### Post by psychobilly freakout on 2009-01-26
This is the only thing i get once i download the flash player:

<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<!-- InstanceBegin template="/Templates/labs_master.dwt" codeOutsideHTMLIsLocked="false" -->
<head>
<!-- Template $Revision: 1.7 $ applied. -->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta http-equiv="Content-Language" content="en-us" />
<link rel="icon" href="/favicon.ico" type="image/x-icon" />
<link rel="shortcut icon" href="/favicon.ico" type="image/x-icon" />
<!-- InstanceParam name="ssi_syntax" type="text" value="#include virtual=" --><!-- InstanceParam name="MMlocale" type="text" value="en_us" --><!-- InstanceParam name="flashdetection" type="boolean" value="true" --><!-- InstanceParam name="fma" type="boolean" value="false" --><!-- InstanceParam name="pod" type="boolean" value="false" --><!-- InstanceParam name="promo" type="boolean" value="false" --><!-- InstanceParam name="infoPod" type="boolean" value="false" --><!-- InstanceParam name="fullwidth" type="boolean" value="false" --><!-- InstanceParam name="dynamicUI" type="boolean" value="true" --><!-- InstanceParam name="popups" type="boolean" value="false" --><!-- InstanceBeginEditable name="head" -->
<title>Adobe Labs - Downloads: Flash Player 10</title>
<link rel="stylesheet" rev="stylesheet" href="/css/handheld.css" type="text/css" media="handheld" charset="utf-8" />
<link rel="stylesheet" rev="stylesheet" href="/css/assistive.css" type="text/css" media="aural, braille, embossed" charset="utf-8" />
<link rel="stylesheet" rev="stylesheet" href="/css/print.css" type="text/css" media="print" charset="utf-8" />
<link rel="stylesheet" rev="stylesheet" href="/css/labs_import.css" type="text/css" media="screen" charset="utf-8" />

<!-- InstanceEndEditable -->
<link rel="stylesheet" rev="stylesheet" href="/css/downloads/downloads.css" type="text/css" media="screen" charset="utf-8" />
<script src="/js/labs_global.js" type="text/javascript" charset="utf-8"></script>
<script src="/js/labs_globalnav.js" type="text/javascript" charset="utf-8"></script>
<script src="/js/dyn_ui.js" type="text/javascript" charset="utf-8"></script>
</head>
<body>
<!--googleoff: index--><ul id="accesslink"><li><a href="/help/accessibility.html" tabindex="1">Accessibility</a></li><li><a href="#depthpath">Skip global navigation</a></li>
</ul><!--googleon: index-->
<div id="labs-globalnav-wrapper">
<dl id="labs-companymenu">
	<dt><a href="http://www.adobe.com/go/labs_gnav_logo">Adobe Labs</a></dt>

	<dd>&nbsp;</dd>
	<dd>&nbsp;</dd>	
</dl>
<ul id="labs-depthpath">
	<li><a href="http://www.adobe.com/">Adobe.com Home</a></li>
	<li><a href="http://www.adobe.com/support/">Support</a></li>
	<li class="last-child"><a href="http://www.adobe.com/devnet/">Developer Centers</a></li>
</ul>
<br class="clear-both" />

<div id="labs-globalnav">
	<ul id="main-labs-nav">
		<li><a href="http://www.adobe.com/go/labs_gnav_home">Home</a></li>
		<li><a href="http://www.adobe.com/go/labs_gnav_technologies">Technologies</a></li>
		<li><a href="http://www.adobe.com/go/labs_gnav_wiki">Wiki</a></li>
		<li><a href="http://www.adobe.com/go/labs_gnav_downloads">Downloads</a></li>
		<li><a href="http://www.adobe.com/go/labs_gnav_community">Community</a></li>

		<li><a href="http://www.adobe.com/go/labs_gnav_rss">RSS Feeds</a></li>
		<li class="last-child"><a href="http://www.adobe.com/go/labs_gnav_about">About Labs</a></li>
	</ul>
<div id="labs-gnav-search">
	<form id="labs-search" name="labs-search" method="get" action="http://www.adobe.com/cfusion/labs/search.cfm" accept-charset="utf-8">
	<input type="hidden" name="loc" value="en_us" />
		<input type="text" class="textfield" name="term" />
		<button name="search" type="submit" id="search-submit">Search</button>

	</form>
</div>
	<img src="/images/labs_master/labs_gnav_capbottom.gif" alt="cap bottom" id="labsnav-capBottom" />
</div>
<ul id="labs-login-nav">
		<li id="greeting">Welcome, <span id="screenName">Guest</span></li>
		<li id="account"><a href="http://www.adobe.com/go/labs_gnav_your_account">Your Account</a></li>
		<li id="signout" class="last-child" style="display: none"><a href="http://www.adobe.com/go/labs_gnav_sign_out">Logout</a></li>

		<li id="signin" class="last-child"><a href="http://www.adobe.com/go/labs_gnav_sign_in">Sign In</a></li>
  </ul>
<script type="text/javascript">
	var screenName = document.getElementById('screenName'),
	signin = document.getElementById('signin'),
	signout = document.getElementById('signout');
	
	if(signin && signout && screenName) {					
		var screenNameValue = adobe.Cookie.get("SCREENNAME"),
		authenticAdobeId = adobe.Cookie.get('AUID');
		
		if(screenNameValue) {
			registerOnReady(function() {
				screenName.innerHTML = screenNameValue;
			});
		}
		
		if(authenticAdobeId) {
			signout.style.display="";
			signin.style.display="none";
		}
	}
</script>
	
	<a name="globalnav" id="globalnav"></a>
	
</div>
	
<div id="layoutLogic" class="partial-width">
  <div id="gecko"><!-- InstanceBeginEditable name="header" -->
    <div id="depthpath">

      <ol>
        <li><a href="/">Home</a></li>
        <li class="last-child"><a href="/downloads/">Downloads</a></li>
      </ol>
    </div>
    <h1>Adobe Labs Downloads </h1>
    <!-- InstanceEndEditable -->

    <div id="contentBody"><!-- InstanceBeginEditable name="content" -->
      <h2>Flash Player 10</h2>
      <p><span class="achtung"><strong>Update</strong></span>: An alpha refresh of 64-bit Adobe Flash Player 10 for Linux operating systems was released on 12/16/2008. Flash Player 10 beta for Solaris was released on 9/26/2008. The release versions of Flash Player 10 for Windows, Macintosh, and 32-bit Linux are now available from the <a href="http://www.adobe.com/go/getflashplayer" target="_blank">Flash Player Download Center</a>. Please download the latest prerelease versions below.</p>
      <p>This is a prerelease version of the Adobe&reg; Flash&reg; Player 10 software for Solaris and 64-bit Linux platforms. It is being made available for developers and consumers to test their content to ensure new features function as expected, existing content plays back correctly, and there are no compatibility issues.</p>

      <p>The Flash Player 10 prerelease is available in all supported languages; however, the prerelease installers are only in English and we can only accept feedback in English at this time.</p>
      <p>Release versions of Flash Player  are  available from the <a href="http://www.adobe.com/go/getflashplayer" target="_blank">Flash Player  Download Center</a> on Adobe.com.</p>
      <h4>Terms of Use</h4>
      <p>Your use of Adobe Labs, including the downloading of software and submission of comments, ideas, feature requests, and techniques, and Adobe’s rights to use such submitted materials are governed by the <a href="http://www.adobe.com/go/labs_term_of_use">Adobe Labs Terms of Use</a> and the <a href="http://www.adobe.com/go/labs_privacy_policy" target="_blank">Adobe Online Privacy Policy</a>. By downloading, copying, or using Adobe software and related materials, you also agree to the appropriate <a href="http://www.adobe.com/products/eulas/players/flash/" target="_blank">Adobe Software License Agreement</a>, including the limitations related to prerelease Software.</p>

      <h3>Flash Player 10 Prerelease</h3>
      <p>The following downloads will install Flash Player 10 prerelease. The beta builds for Solaris were released on September 26, 2008. The 64-bit Flash Player 10 alpha refresh for Linux was released on December 16, 2008.</p>
      <p><span class="achtung"><strong>Important:</strong></span> All users should uninstall any currently installed Flash Player before installing the latest prerelease.</p>
      <h4>English</h4>
      <ul class="iconmarker-16x16 stamp-fileinfo">
        <li><img src="/images/icons/download.gif" alt="dl" width="16" height="16" align="absmiddle" /><a href="http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz">Download 64-bit Plugin for Linux</a> (TAR.GZ, 3.54 MB)</li>

        <li><img src="/images/icons/download.gif" alt="dl" width="16" height="16" align="absmiddle" /><a href="http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_solaris_x86_092608.tar.bz2">Download Plugin for Solaris-x86</a> (TAR.BZ2, 4.06 MB)</li>
        <li><img src="/images/icons/download.gif" alt="dl" width="16" height="16" align="absmiddle" /><a href="http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_solaris_sparc_092608.tar.bz2">Download Plugin for Solaris-Sparc</a> (TAR.BZ2, 4.39 MB)</li>
      </ul>
      <!-- InstanceEndEditable --></div>
  </div>
  <br />

  <!-- extra break for opera 7 bug -->
</div>
<div id="capBottom">&nbsp;</div>
<!--googleoff: index-->
<!-- global footer $Revision: 1.9.28.1 $ -->
<div id="contentFooter">
	<div id="copyright-terms">
        <p><a href="http://labs.adobe.com/">Home</a> | <a href="http://labs.adobe.com/technologies/">Technologies</a> | <a href="http://labs.adobe.com/wiki/">Wiki</a> | <a href="http://labs.adobe.com/downloads/">Download</a> | <a href="http://labs.adobe.com/community/">Community</a> | <a href="http://labs.adobe.com/showcase/">Showcase</a> | <a href="http://labs.adobe.com/rss_feeds/">RSS Feeds</a> | <a href="http://www.adobe.com/cfusion/labs/search.cfm">Search</a> | <a href="http://labs.adobe.com/about/">About Adobe Labs</a> | <a href="http://www.adobe.com/">Adobe.com Home</a> | <a href="http://www.adobe.com/support/">Support</a> | <a href="http://www.adobe.com/devnet/">Developer Connection</a></p>

        <br />
        <p>Copyright &copy; 2009 Adobe Systems Incorporated. <a href="http://www.adobe.com/misc/copyright.html">All rights reserved</a>.
        <br />
        Your use of the Adobe Labs including the download of software, submission of comments, ideas, feature requests and techniques, and Adobe's rights to use such submitted materials, is governed by the <a href="http://www.adobe.com/go/labs_term_of_use">Adobe Labs Terms of Use</a> and the <a href="http://www.adobe.com/go/labs_privacy_policy">Adobe Privacy Policy</a>.</p>

        <p>Search powered by<a href="http://www.google.com/" target="new"><img class="googlelogo" src="/images/labs_master/logo_google.gif" width="43" height="18" alt="Powered by Google" /></a></p>
	</div>	
	<br class="clear-both" />
</div>
<!--googleon: index-->

<!-- InstanceBeginEditable name="analytics" -->
<div style="display: none;"><!-- SiteCatalyst code version: G.9.
Copyright 2002 Omniture, Inc. More info available at
[http://www.omniture.com](http://www.omniture.com) -->
<script language="JavaScript" type="text/javascript"><!--
var s_code=' '//--></script>
<script language="JavaScript" src="/uber/js/omniture_s_code.js" type="text/javascript"></script>
<script language="JavaScript" type="text/javascript"><!--
var s_accountName;
var s_docHost = window.location.hostname.toLowerCase();
var s_docURL = window.location.pathname.toLowerCase();

if (!!window.adobe) {
  var sc_iFrame=adobe.Cookie.get("adobe.omniture.save");
}
if (!!sc_iFrame && (sc_iFrame.indexOf("initialLoad") != -1) && (s_docURL.indexOf("/ssi/iframe/") != -1))  {
}
else {
if ((s_docHost.indexOf(".dev.adobe.") != -1) || (s_docHost.indexOf("stage.") != -1) || (s_docHost.indexOf("staging.") != -1) || (s_docHost.indexOf(".sea.adobe") != -1) || (s_docHost.indexOf(".corp.adobe") != -1)) {  s_accountName="mxadobetest";
}
else {
  s_accountName="mxmacromedia";
}
if (s_docURL.indexOf("/devnet/") != -1) {
  s_channel="DevNet";
  // Track Tabs as Pages when targeted directly
  if (document.URL.indexOf("navID=") != -1) {
    var s_pairs = window.location.search.substring(1).split("&");
	for (i=0;i<s_pairs.length;i++) {
	  if (s_pairs[i].indexOf("navID=") != -1)
  		s_pageName=document.URL.substring(0, document.URL.indexOf("?")+1) + s_pairs[i];
		s_pageName=s_pageName.toLowerCase();
	}
  }
}
else if (s_docHost.indexOf("help.adobe.com") != -1) {
  // Tracking Learning Resources help.adobe.com
  s_channel="Support Help.adobe.com";
  var s_title=document.title;
  if (s_title.indexOf("*") != -1) { 
    s_title=document.title.substring(0,document.title.indexOf("*"));
  }
  s_pageName="Support help.adobe.com: " + s_title;
  s_prop23=document.URL.toLowerCase();
}
else if (s_docHost.indexOf("kb.adobe.com") != -1) {
  s_channel="Support Knowledgebase";
  if (s_docURL.indexOf("searchentry.do") != -1) {
  	try {
		var SearchStringValue = adobe.Element.getElementsByClassName($("simple-options"),"input","textfield")[0].value;
		var s_prop11=SearchStringValue.toLowerCase();
		var s_eVar21=s_prop11;
	} catch (ex) { 
	}
  }
  else if (s_docURL.indexOf("microsite.do") != -1) {
     var s_pageName = document.URL.toLowerCase();
     if (s_pageName.indexOf(';') != -1) {
       s_pageName=s_pageName.substring(0,s_pageName.indexOf(';'));
     }
  }
}
else if (s_docURL.indexOf("/designcenter/") != -1) {
  s_channel="Adobe Design Center";
  if (s_docURL.indexOf("/articles/") != -1) {
    mymetatags = document.getElementsByTagName("meta");
	var adc_Title=s_docURL;
	var adc_Products="";
	var adc_Topics="";
	var adc_Type="";
	for (i=0;i < mymetatags.length;i++)  {
		if (mymetatags[i].getAttribute("name") == "product") {
		   if (mymetatags[i].getAttribute("content").indexOf("[product") == -1)
		     adc_Products=(adc_Products=="")?';'+mymetatags[i].getAttribute("content"):adc_Products+',;'+mymetatags[i].getAttribute("content"); 
		}
		else if (mymetatags[i].getAttribute("name") == "topic") {
			adc_Topics=(adc_Topics=="")?mymetatags[i].getAttribute("content"):adc_Topics+','+mymetatags[i].getAttribute("content");
		}
		else if (mymetatags[i].getAttribute("name") == "columntype") {
			adc_Type=mymetatags[i].getAttribute("content");
		}
	}
	var s_eVar22=adc_Title;
	if (adc_Type != "") var s_eVar23=adc_Type;
	if (adc_Topics != "") var s_eVar24=adc_Topics;
	if (adc_Products != "") {
	  var s_products=adc_Products;
	  var s_events="event12";
	}
   }    
}
	if (!window.scMMInclude) {
		var s_wd=window,s_tm=new Date;
		if(s_code!=' '){
			s_code=s_dc(s_accountName);
		    if(s_code)document.write(s_code)
		} 
	} else {
		  s_wds(s_accountName);s_ca(s_accountName); 
  	}	
}
function sendAnalyticsEvent(str){var ns=s_accountName;if(str!=null)ns+=","+str;void(s_gs(ns));}
function sendLinkEvent(accnt,lnkname,type){
accnt=s_accountName;s_linkType=type;s_lnk=true;s_linkName=lnkname;void(s_gs(accnt));}
//--></script><noscript><img
src="http://stats.adobe.com/b/ss/mxmacromedia/1/G.9-XELvs" height="1" width="1" border="0" alt="" /></noscript><!--/DO NOT REMOVE/-->

<!-- End SiteCatalyst code version: G.6. -->
</div>
<noscript>
<!--[if lt IE 7]><link href="/css/master_import/noscript_ie6.css" type="text/css" rel="stylesheet" /><![endif]-->
<!--[if IE 7]><link href="/css/master_import/noscript_ie7.css" type="text/css" rel="stylesheet" /><![endif]-->
</noscript>
<!-- InstanceEndEditable --><img id="flash_pixel" name="flash_pixel" src="/images/pixel.gif" width="1" height="1" alt="" />
</body>
<!-- InstanceEnd -->
</html>

---

### Post by igknighted on 2009-01-26
> **psychobilly freakout said:**
> Ok

None of these downloads are not working properly, i am downloading the links that you guys are providing and when it's done i got to launch application and press ok and it goes onto the desktop.And when i try to open to file it says"could not display jre-6ul...3-linux-amd64-22_dec_2008.bin"
"the location is not a folder"

I've tried to download all other files from the java website and i keep getting the same thing.

You can't click to launch the files.  You must use the CLI to install them.  Follow the steps Codename listed above (note that he/she called his file java.bin, you should substitute the name of your file, which will certainly be different).

EDIT: Direct link to flash player: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

EDIT2: Extract the flash file, and move it to the folder /home/<your username>/.mozilla/plugins.  Then restart firefox, and flash should work.

---

### Post by psychobilly freakout on 2009-01-26
> **igknighted said:**
> You can't click to launch the files.  You must use the CLI to install them.  Follow the steps Codename listed above (note that he/she called his file java.bin, you should substitute the name of your file, which will certainly be different).

EDIT: Direct link to flash player: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

EDIT2: Extract the flash file, and move it to the folder /home/<your username>/.mozilla/plugins.  Then restart firefox, and flash should work.

Ok now the flash player is up and running, now Java is the only thing left and im trying my best to find multiple ways in getting it but nothing seems to work.

---

### Post by ZhuaSD on 2009-02-03
Ok, that is progress, good to see.

So how is the java install going?  Are you getting error messages?

---

### Post by grewolf on 2009-02-06
> **Codename said:**
> So download the latest version from Java right here: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp). My instructions are going to assume you're going to save it to your desktop and the file name is "java.bin". So what you want to do is navigate to the Terminal and run these commands:
```
cd ~/Desktop
chmod +x java.bin
sudo mv java.bin /opt
cd /opt
sudo ./java.bin

```
Once you've done that it will start unzipping the files in the /opt directory, there should be a new directory, and not sure what it would be called, but navigate to it:
```
cd jre_directory/bin
sudo ln -s /opt/jre_directory/bin/java /usr/local/bin/java
```
There's also instructions on Java's website if you don't understand mine, but if you followed mine, that should get Java up and running.

I used your instructions and Frostwire now works for me but it seems that I am still using update 10 when I am using firefox.  Was wondering how to change this?

---

