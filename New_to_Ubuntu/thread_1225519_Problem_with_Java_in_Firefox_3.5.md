---
title: "Problem with Java in Firefox 3.5"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2009-07-28
I recently upgraded to Shiretoko (FF 3.5) and have not been able to view anything that uses Java. I first noticed it when I went to [http://www.minecraft.net/](http://www.minecraft.net/) and then noticed it whenever I go to pogo games as well. I checked the about: plugins in firefox but it showed that all of the java plugins were enabled. I have been googling trying to find a solution but I haven't found anything of help yet. I am using Ubuntu 9.04 64bit btw. If anyone could point me in the right direction I would be much obliged.

---

### Post by Jimleko211 on 2009-07-28
Try reinstalling the Sun JRE.  I had that problem once and that fixed it.

---

### Post by skaldicpoet9 on 2009-07-28
Yeah, I just tried that but it didn't work. Thanks for the reply though :)

note: whenever I go to Java.com to detect my installation the page just doesn't display a message that I don't have Java installed, it just sits there loading.

---

### Post by skaldicpoet9 on 2009-07-28
Is there an error console or some such thing that I could post here that might help with solving this problem? I am really racking my brain over this one...

---

### Post by ketedford on 2009-07-28
Being new, I don't know exactly why this fixed my issues. However, I was having major problems with mycokerewards.com and not being able to log in. Posted a couple times on this site and couldn't get it figured out. 

Kept digging and found 

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002&page=2](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002&page=2) 

If you go to post #1, it is extremely long and has many topics. However, I believe that the part I did was:
_____________________________________
**Solution** [*FOT004*]**:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

 	Code:
 	sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 

**Symptoms:**

[LIST]
[*] **Web sites keeps loading but never show up**
[*] **Firefox can't connect to any sites, but other browsers work**
[*] **Firefox can connect to sites only using the IP number**
[*] **Connections settings are reset after restart**
[/LIST]

**Solution** [*FOT005*]**:**

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). If the settings reset after restart, then delete the file *user.js* from the profile folder, to reset proxy settings.

Additionally, disable ipv6 on Firefox Preferences, by setting the *network.dns.disableIPv6* preference to **true**.

   1. Type *about:config* in the address bar, press Enter.
   2. Find *network.dns.disableIPv6* in the list.
   3. Right-click -> Toggle.
   4. Restart your Mozilla application and try again. 
____________________________________________

Immediately after, I went to the mycokerewards.com site and it worked like a champ and is still working. 

Also, I went to the site you referenced and it also works. Good luck and let me know.

:D

---

### Post by skaldicpoet9 on 2009-07-29
Thanks for the suggestion but I don't think that would help me much. The problem isn't my flash plugin (which works just fine) it is my Java installation. Like I said before, when I go to Java.com the site doesn't even recognize that I have Java installed (even though I do, I checked in the package manager). I think perhaps I might just reinstall Java and see if that helps at all. I really don't know what to do. I know it is my Java but I don't know a clearer solution then to just reinstall. I wish I could just figure out what the real problem was.

---

### Post by skaldicpoet9 on 2009-07-29
> **ketedford said:**
> 
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 



Hmm, this actually worked for me, not to enable Java but unbeknownst to be Flash wasn't working as well. Thanks for the info :)

Does anyone else know how to get my Java enabled though? I still can't use anything that uses Java.

---

### Post by DrTaylor on 2009-08-01
Me too. Exact same problem. It's really annoying. Everyone's using Java.

---

### Post by Malta paul on 2009-08-01
You might like to try a java plugin:
[https://addons.mozilla.org/en-US/firefox/search?q=java&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=java&cat=all)

They work good for me :D

---

### Post by DrTaylor on 2009-08-01
No luck, but thanks. Does anyone else have this problem?

---

### Post by sandeepjshenoy on 2009-08-02
I had the same problem. Here's what I did
Goto to synaptic package manager and search for "jre". Remove all installed versions of java. Now install the following:
sun-java6-jre
sun-java6-bin
sun-java6-fonts
sun-java6-plugin

Hope this works for you...

---

### Post by fsando on 2009-08-03
> **sandeepjshenoy said:**
> I had the same problem. Here's what I did
Goto to synaptic package manager and search for "jre". Remove all installed versions of java. Now install the following:
sun-java6-jre
sun-java6-bin
sun-java6-fonts
sun-java6-plugin

Hope this works for you...

I've got the exact same problem - can't access my web bank.

Latest example is this site. It's a web conferencing service that offers full Linux support via java. Unfortunately it crashes Firefox when you press the button 'Host A Meeting'. It works perfectly under Windows.

[https://www.yugma.com/](https://www.yugma.com/)

EDIT:
I've dug up something I believe is important - but I will investigate further.

I appears that it crashes because it tries to access a java security module from Microsoft that isn't present.

To see what happened:
First I changed settings for java to open console and allow logging that's in
```
System > Preferences > Sun Java 6 Plugin Control Panel
```
Under 'Advanced' I set it to Show Console  and enabled all debug options (don't know how to use them yet, though)

Then when accessing the above site pressing 'Host a meeting' I get the following in the console before crashing
```

Java Plug-in 1.6.0_14
Using JRE version 1.6.0_14-b08 Java HotSpot(TM) Client VM
User home directory = /home/finn


network: Loading user-defined proxy configuration ...
network: Done.
network: Loading proxy configuration from Netscape Navigator ...
network: Error reading registry file: /home/finn/.mozilla/appreg
network: Done.
network: Loading browser proxy configuration ...
network: Done.
network: Proxy Configuration: Browser Proxy Configuration


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

basic: New window ID: 2a017b2
basic: Value of xembed: 1
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@10b4b2f, refcount=1
basic: setWindow: call before applet exists:2a017b2
security: Accessing keys and certificate in Mozilla user profile: null
security: JSS is not configured
basic: Added progress listener: sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@20be79
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: completed perf rollup
security: Blacklist revocation check is enabled
cache: Skip blacklist check as cached value is ok.
network: Cache entry found [url: https://www.yugma.com/app/installer/v4/InstallerApplet260309.jar, version: null]
Reading certificates from 5726 https://www.yugma.com/app/installer/v4/InstallerApplet260309.jar | /home/finn/.java/deployment/cache/6.0/4/7fca79c4-36c1c949.idx
security: Loading Root CA certificates from /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/security/cacerts
security: Loaded Root CA certificates from /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/security/cacerts
security: Loading Deployment certificates from /home/finn/.java/deployment/security/trusted.certs
security: Loaded Deployment certificates from /home/finn/.java/deployment/security/trusted.certs
security: Loading certificates from Deployment session certificate store
security: Loaded certificates from Deployment session certificate store
security: Validate the certificate chain using CertPath API
security: Obtain certificate collection in Root CA certificate store
security: Obtain certificate collection in Root CA certificate store
security: No timestamping info available
security: Found jurisdiction list file
security: Start checking trusted extension for this certificate
security: Start comparing to jurisdiction list with this certificate
security: The CRL support is disabled
security: The OCSP support is disabled
security: Checking if certificate is in Deployment denied certificate store
security: Checking if certificate is in Deployment permanent certificate store
network: Cache entry not found [url: https://www.yugma.com/app/installer/v4/com/ms/security/PolicyEngine.class, version: null]
network: Connecting https://www.yugma.com/app/installer/v4/com/ms/security/PolicyEngine.class with proxy=DIRECT
network: Connecting socket://www.yugma.com:443 with proxy=DIRECT
security: Loading Root CA certificates from /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/security/cacerts
security: Loaded Root CA certificates from /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/security/cacerts
security: Loading SSL Root CA certificates from /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/security/cacerts
security: Loaded SSL Root CA certificates from /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/security/cacerts
security: Loading certificates from Deployment session certificate store
security: Loaded certificates from Deployment session certificate store
security: Checking if certificate is in Deployment denied certificate store
network: Connecting https://www.yugma.com/app/installer/v4/com/ms/security/PolicyEngine.class with cookie "__utma=264726023.4582243354054571000.1249248131.1249301931.1249303692.5; __utmz=264726023.1249248131.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); AWSUSER_ID=awsuser_id1249248236672r7511; __utmb=264726023.2.10.1249303692; AWSSESSION_ID=awssession_id1249301318880r2975; PHPSESSID=kuvhmq6a5go70u484eoj2g30e6; __utmc=264726023"
com.ms.security class not found exception :java.lang.ClassNotFoundException: com.ms.security.PolicyEngine
liveconnect: the url of the applet is https://www.yugma.com and the permission is = true

```

A google search for 'com.ms.security' comes up with the following

[http://java.sun.com/j2se/1.4.2/docs/guide/deployment/deployment-guide/upgrade-guide/article-05.html](http://java.sun.com/j2se/1.4.2/docs/guide/deployment/deployment-guide/upgrade-guide/article-05.html)

Excerpt:
> java.lang.ClassNotFoundException thrown on com.ms.security package when applet runs

Symptoms

    When running an applet in a browser using the Sun JRE, a ClassNotFoundException is thrown by the ClassLoader on the com.ms.security package. The same applet runs under the Microsoft VM.

Cause

    The Microsoft VM provides the proprietary com.ms.security package for applets and applications to access the security policy at runtime. This package is not available in the Sun JRE, so a ClassNotFoundException is thrown when the applet runs.

Resolution

    The workaround is to migrate the applet source from using the com.ms.security package to using similar classes in the java.security package.
[...]


---

### Post by fsando on 2009-08-03
I don't think the above was the reason now I think it is likely to be javascript related

This is the console output of another java app that loads successfully

```

[...]
security: Checking if certificate is in Deployment denied certificate store
security: Checking if certificate is in Deployment permanent certificate store
liveconnect: the url of the applet is https://web41.prod.bec.dk and the permission is = true
liveconnect: JavaScript: calling Java system code
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JSObject::call: name=BECClearAlert
[...]

```

And this is the same applet when it crashes:

```

[...]
security: Checking if certificate is in Deployment denied certificate store
security: Checking if certificate is in Deployment permanent certificate store
liveconnect: the url of the applet is https://web41.prod.bec.dk and the permission is = true

```
As you can see it never gets to the javascript part

---

### Post by emeraldgirl08 on 2009-08-03
My Java shows up on verify Java version as Version 6 Update 14.

I know that when I installed all the restricted extras I saw the SunJava stuff being downloaded and then installed. It even asked me to choose "Yes" or "No" on an License Agreement (or something like that).

I'm not sure what the process would be for you to install this but this post helped me out.

[Comprehensive Multimedia and Video How to.]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by j_boggs on 2009-08-04
> **sandeepjshenoy said:**
> I had the same problem. Here's what I did
Goto to synaptic package manager and search for "jre". Remove all installed versions of java. Now install the following:
sun-java6-jre
sun-java6-bin
sun-java6-fonts
sun-java6-plugin

Hope this works for you...

This solved my problems with Java.  Thank you sandeepjshenoy!

---

### Post by DrTaylor on 2009-08-07
Yay! It now works. Thank you.

---

### Post by speedwell68 on 2009-08-17
> **sandeepjshenoy said:**
> I had the same problem. Here's what I did
Goto to synaptic package manager and search for "jre". Remove all installed versions of java. Now install the following:
sun-java6-jre
sun-java6-bin
sun-java6-fonts
sun-java6-plugin

Hope this works for you...

This worked a treat.  Thank you very much.

---

### Post by Jose Catre-Vandis on 2009-09-05
> **sandeepjshenoy said:**
> I had the same problem. Here's what I did
Goto to synaptic package manager and search for "jre". Remove all installed versions of java. Now install the following:
sun-java6-jre
sun-java6-bin
sun-java6-fonts
sun-java6-plugin

Hope this works for you...

Fixed things for me too :)

---

