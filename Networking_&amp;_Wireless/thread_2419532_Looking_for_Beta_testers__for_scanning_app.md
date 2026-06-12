---
title: "Looking for Beta testers  for scanning app"
date: 2019-05-23
forum: Networking &amp; Wireless
---

### Post by markosjal on 2019-05-23
I have a scanning app I created that runs on Ubuntu (or other linux), Apache (possibly other web servers???)  PHP , Avahi daemon. I am looking for two different types of beta testers as  detailed below. The app is a scanning app. 

These days, many  network connected multifunction devices ae Apple AirScan protocol compatible. 

IMHO SANE can be very problematic not to mention HPLIP and the like . It seems Fred, Wilma,  Barney and Betty that program SANE have trouble recognizing that there is "driverless scanner support" these days. The problems with HPLIP and other proprietary solutions even complicate matters more. There ks no longer a need to support most newer network scanners through "drivers".


The app I created does two things

1st with some non AirScan Scanners it should add Airscan compatibility (untested on iOS or OSX) . This part is compatible only with the following scanners, but hoping to add more:
ION AirCopy
ION AirCopy E-Post Edition
Halo Magic Scanner
Mustek iScan Air / S400W
Century CPS-A4WF
iScan Fly
Transcription Patri Kun A4 Wi-Fi Portable Scanner
&#36578;&#20889;&#12497;&#12483;&#12488;&#12522;&#12367;&#12435; A4 Wi-Fi&#12509;&#12540;&#12479;&#12502;&#12523;&#12473;&#12461;&#12515;&#12490;&#12540;

The group of above scanners are all the same with different labels. This was the reason I started this. Not long after  starting it, I realized the ability to use other command line scanners like some eSCL/Airscan scanner command line tools that run under Python but up to now they are too unreliable so I wrote my own code to support these eSCL/AirScan scanners in PHP.


**Beta testers Group 1**
Would have one of the following scanners and at least one Apple Device with current iOS or OSX
ION AirCopy
ION AirCopy E-Post Edition
Halo Magic Scanner
Mustek iScan Air / S400W
Century CPS-A4WF
iScan Fly
Transcription Patri Kun A4 Wi-Fi Portable Scanner
&#36578;&#20889;&#12497;&#12483;&#12488;&#12522;&#12367;&#12435; A4 Wi-Fi&#12509;&#12540;&#12479;&#12502;&#12523;&#12473;&#12461;&#12515;&#12490;&#12540;
For this group I need to know how the airscan functionalty work sand to test the Web GUI . So far I have tested only with VueScan which detected and used the scanner without issues with my software. This also involves testing the Web GUI 

**Beta Testers Group 2**
Should have any AirScan/eSCL protocol scanner to primarily to test compatibility with these scanners and to test the Web GUI 

**For either Group 1 or 2** 
you should have a Linux x86 or x86-64 server or workstation with Apache2 PHP 7 or higher, some knowledge of configuring Apache and PHP , knowledge of creating user accounts .  A reliable LAN, some time to do testing.

Beta users will be rewarded with a copy of the full product when completed. The current beta has known issues with file conversions still.

reply to markosjal at the email with a G if interested,

---

