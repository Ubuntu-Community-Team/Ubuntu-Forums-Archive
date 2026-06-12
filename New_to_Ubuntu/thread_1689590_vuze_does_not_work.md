---
title: "vuze does not work"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by liatodua on 2011-02-17
Hi,

I used to use vuze software on Windows. So now when I have lubuntu I downloaded linux version of vuze and installed as it was explained in the README file. It added vuze icon to the Application>Internet menu and when I click it vuze window opens. It definitely lacks some of the features I was used to. But the main thing is that it can not find anything on web! Meaning it does not work.

I looked around and discovered that there is a new icon added to Applications>Preferences menu called "OpenJDK Java 6 Policy Tool" and when I tried it the only thing which was possible to open was a warning log saying: 

java.io.FileNotFoundException: /home/liatodua/.java.policy (No such file or directory)

I also looked around and find debug-log file of the vuze and it consists of repetitions of texts I pasted below (sorry for the big citation).

Could anybody explain please what is the problem and how can I make vuze work?


[2/16/11 5:48 PM] Log File Opened for Vuze 4.3.0.6
[17:48:04] DEBUG::Wed Feb 16 17:48:04 GET 2011  Successfully migrated key management
[17:48:37] [stderr] DEBUG::Wed Feb 16 17:48:37 GET 2011::com.aelitis.azureus.core.versioncheck.VersionCheckClient$2::run::189:
[17:48:37] DEBUG::Wed Feb 16 17:48:37 GET 2011::com.aelitis.azureus.core.versioncheck.VersionCheckClient$2::run::189:
[17:48:37] [stderr]   Timeout waiting for version check to complete
[17:48:37]   Timeout waiting for version check to complete
[17:48:37] [stderr]     UtilitiesImpl$DelayedTaskImpl::run::1316,UtilitiesImpl$7::run::979,AEThread2$threadWrapper::run::287
[17:48:37]     UtilitiesImpl$DelayedTaskImpl::run::1316,UtilitiesImpl$7::run::979,AEThread2$threadWrapper::run::287
[17:49:04] [stderr] DEBUG::Wed Feb 16 17:49:04 GET 2011::com.aelitis.azureus.core.versioncheck.VersionCheckClient::preProcessReply::1005:
[17:49:04] DEBUG::Wed Feb 16 17:49:04 GET 2011::com.aelitis.azureus.core.versioncheck.VersionCheckClient::preProcessReply::1005:
[17:49:04] [stderr]   com.aelitis.azureus.core.networkmanager.admin.NetworkAdminException: DNS query failed
[17:49:04] [stderr] 	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookupDNS(NetworkAdminASNLookupImpl.java:255)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookupDNS(NetworkAdminASNLookupImpl.java:163)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookup(NetworkAdminASNLookupImpl.java:72)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminImpl.lookupCurrentASN(NetworkAdminImpl.java:1460)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.preProcessReply(VersionCheckClient.java:983)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeHTTP(VersionCheckClient.java:715)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:588)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:313)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:229)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:211)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.versioncheck.VersionCheckClient$2$1.run(VersionCheckClient.java:178)
[17:49:04] [stderr] 	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
[17:49:04] [stderr] Caused by: javax.naming.CommunicationException: DNS error [Root exception is java.net.SocketTimeoutException: Receive timed out]; remaining name '157.187.134.178.origin.asn.cymru.com'
[17:49:04] [stderr] 	at com.sun.jndi.dns.DnsClient.query(DnsClient.java:300)
[17:49:04] [stderr] 	at com.sun.jndi.dns.Resolver.query(Resolver.java:81)
[17:49:04] [stderr] 	at com.sun.jndi.dns.DnsContext.c_getAttributes(DnsContext.java:430)
[17:49:04] [stderr] 	at com.sun.jndi.toolkit.ctx.ComponentDirContext.p_getAttributes(ComponentDirContext.java:231)
[17:49:04] [stderr] 	at com.sun.jndi.toolkit.ctx.PartialCompositeDirContext.getAttributes(PartialCompositeDirContext.java:139)
[17:49:04] [stderr] 	at com.sun.jndi.toolkit.ctx.PartialCompositeDirContext.getAttributes(PartialCompositeDirContext.java:127)
[17:49:04] [stderr] 	at javax.naming.directory.InitialDirContext.getAttributes(InitialDirContext.java:140)
[17:49:04] [stderr] 	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookupDNS(NetworkAdminASNLookupImpl.java:215)
[17:49:04] [stderr] 	... 11 more
[17:49:04] [stderr] Caused by: java.net.SocketTimeoutException: Receive timed out
[17:49:04] [stderr] 	at java.net.PlainDatagramSocketImpl.receive0(Native Method)
[17:49:04] [stderr] 	at java.net.AbstractPlainDatagramSocketImpl.receive(AbstractPlainDatagramSocketImpl.java:127)
[17:49:04] [stderr] 	at java.net.DatagramSocket.receive(DatagramSocket.java:729)
[17:49:04] [stderr] 	at com.sun.jndi.dns.DnsClient.doUdpQuery(DnsClient.java:411)
[17:49:04] [stderr] 	at com.sun.jndi.dns.DnsClient.query(DnsClient.java:203)
[17:49:04] [stderr] 	... 18 more
[17:49:04] [stderr] 
[17:49:04]   com.aelitis.azureus.core.networkmanager.admin.NetworkAdminException: DNS query failed
	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookupDNS(NetworkAdminASNLookupImpl.java:255)
	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookupDNS(NetworkAdminASNLookupImpl.java:163)
	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookup(NetworkAdminASNLookupImpl.java:72)
	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminImpl.lookupCurrentASN(NetworkAdminImpl.java:1460)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.preProcessReply(VersionCheckClient.java:983)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.executeHTTP(VersionCheckClient.java:715)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:588)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfoSupport(VersionCheckClient.java:313)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:229)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:211)
	at com.aelitis.azureus.core.versioncheck.VersionCheckClient$2$1.run(VersionCheckClient.java:178)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
Caused by: javax.naming.CommunicationException: DNS error [Root exception is java.net.SocketTimeoutException: Receive timed out]; remaining name '157.187.134.178.origin.asn.cymru.com'
	at com.sun.jndi.dns.DnsClient.query(DnsClient.java:300)
	at com.sun.jndi.dns.Resolver.query(Resolver.java:81)
	at com.sun.jndi.dns.DnsContext.c_getAttributes(DnsContext.java:430)
	at com.sun.jndi.toolkit.ctx.ComponentDirContext.p_getAttributes(ComponentDirContext.java:231)
	at com.sun.jndi.toolkit.ctx.PartialCompositeDirContext.getAttributes(PartialCompositeDirContext.java:139)
	at com.sun.jndi.toolkit.ctx.PartialCompositeDirContext.getAttributes(PartialCompositeDirContext.java:127)
	at javax.naming.directory.InitialDirContext.getAttributes(InitialDirContext.java:140)
	at com.aelitis.azureus.core.networkmanager.admin.impl.NetworkAdminASNLookupImpl.lookupDNS(NetworkAdminASNLookupImpl.java:215)
	... 11 more
Caused by: java.net.SocketTimeoutException: Receive timed out
	at java.net.PlainDatagramSocketImpl.receive0(Native Method)
	at java.net.AbstractPlainDatagramSocketImpl.receive(AbstractPlainDatagramSocketImpl.java:127)
	at java.net.DatagramSocket.receive(DatagramSocket.java:729)
	at com.sun.jndi.dns.DnsClient.doUdpQuery(DnsClient.java:411)
	at com.sun.jndi.dns.DnsClient.query(DnsClient.java:203)
	... 18 more

[18:08:50] [stderr] ERROR: Trying to attach top of widget 'SWTSkinObjectBasic {Search/main.area.searchresultstab/v=searchresults-area, container; parent=Contents.Search.10}' to non-existant widget 'main.area.maintabs'.  Attachment Parameters: main.area.maintabs,10

---

### Post by mick222 on 2011-02-17
I've not used this since it was azureus It didn't include many of the features of the windows version then.Transmission should be installed on your system for managing bit torrents.
   I think Vuze might require sun java you could try using synaptic to remove open jdk and the iced tea plugin and installing sun jave jdk an the sun mozzilla plugin instead. Make sure the partner repositories is enabled in synaptic settings to install sun java.
 By the way how did you install i would always use synaptic or software centre if possible.

---

### Post by liatodua on 2011-02-17
> **mick222 said:**
> I've not used this since it was azureus It didn't include many of the features of the windows version then.Transmission should be installed on your system for managing bit torrents.
   I think Vuze might require sun java you could try using synaptic to remove open jdk and the iced tea plugin and installing sun jave jdk an the sun mozzilla plugin instead. Make sure the partner repositories is enabled in synaptic settings to install sun java.
 By the way how did you install i would always use synaptic or software centre if possible.

I am not sure how to use Transmission. So I preferred Vuze which I was used to. And there is a linux version available. I downloaded it from [http://linux.softpedia.com/get/Multimedia/Video/Vuze-27980.shtml](http://linux.softpedia.com/get/Multimedia/Video/Vuze-27980.shtml)
then extracted and looked at README file. It says:

REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.

I have just recent lubuntu which comes with Openjava 6, yes? So I decided I do not need reinstalling Java. Hopefully it is somewhere in "usual" place. So I did not change the script. I just changed the name of the extracted directory to "Azureus" and cd to it and entered command "azureus" to make the script run. The smart terminal replied that instead I should write "sudo apt-get install azureus". I did that and the installation started. That's it. But the program is dead!

---

### Post by cjv8888 on 2011-02-17
Vuze is in the repositories.  I think you should just reinstall it from there.  It will satisfy all the dependencies automatically.

---

### Post by liatodua on 2011-02-17
> **cjv8888 said:**
> Vuze is in the repositories.  I think you should just reinstall it from there.  It will satisfy all the dependencies automatically.

O, so simple! I reinstalled it from the depository and it started working! Still writes some errors but nevertheless - it works.

Thanks!

---

### Post by FacesComix on 2011-02-26
I'm looking for the convert and UPnP abilities in 4.6... The software center only has 4.3... Does 4.3 have that ability?

---

