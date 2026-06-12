---
title: "Lucid proxy problem."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Gone fishing on 2010-05-01
I connect to the internet through a proxy. I’ve put the proxy settings in Network Proxy and applied system wide, I’ve also added the proxy settings in synaptic.

OK the problem if I run 

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

to set up the mediubuntu repositories it fails however if I

```
sudo –i
```

then

```
wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

it works. If I try and install flashplugin-nonfree using synaptic it fails when it tries to run the script to down load and install the plugin same with ```
sudo apt-get install flashplugin-nonfree
``` however, ```
sudo –i
``` then ```
apt-get install flashplugin-nonfree  works.
```

Now the bit that baffles me however,  sudo apt-get update works fine

Why? is this a bug?

---

### Post by Gone fishing on 2010-05-02
bump

Sorry I just want to know if I'm being stupid before I consider filling a bug report

fails means that it fails to use the proxy settings and I get a resolve error for eg > unable to resolve host address `[www.medibuntu.org](www.medibuntu.org)'

---

### Post by Krieg on 2010-05-03
I have the same problem.   wget gives you problems because the environment variable "no_proxy" has a trailing comma at the end, but even when you get wget to work apt-get will not use the proxy settings.

To make things worse, now Synaptic has its own proxy setting, I don't know why, but it is like that.   After setting the proxy parameters in Synaptic it will work if you use Synaptic but the command line (apt-get) will still not work.

Frustrating.   An LTS that does not let you install packages if you are behind a proxy.

---

### Post by jonvel on 2010-05-03
It's not just a wget problem.  It seems hit-or-miss as to whether the proxy settings are observed.  I've set http_proxy in various places, I've manually set the proxy settings in others.

I've also set the System -> Preferences -> Network Proxy
to what it's supposed to be, and none of it works.  I can't get Firefox to work with "use system settings".  I can't get Google Chrome to work at all with that.

I don't remember having this many issues with 9.10...

---

### Post by Krieg on 2010-05-04
OK, I managed to get apt-get to use the proxy.   I went to: System / Preferences / Network Proxy and clicked on "Apply System Wide".

It seems we are going more into the MS Windows "OK vs Apply" way.

The variable $http_proxy is not respected.  Quite complicated when you do not have GUI

---

### Post by stats on 2010-05-04
I have the same issue as Gone Fishing. I have set proxy settings in .bashrc for user and root, and have also applied them system-wide.

I have noticed that when I run ```
sudo command
``` it fails to use the proxy. running the same command as user and as root work fine.
sudo echo $http_proxy however returns the correct value.

This should be reported as a bug. Things work fine in 9.10

---

### Post by vredley on 2010-05-04
[https://bugs.launchpad.net/ubuntu/+source/wget/+bug/554068](https://bugs.launchpad.net/ubuntu/+source/wget/+bug/554068)

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/556293](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/556293)

Please add a 'me too'.

---

### Post by appier on 2010-05-04
Same problem here.  I am also having trouble getting it to work with:

export http_proxy="http://username:password@my.proxy.org:port"

It worked with previous releases.

---

### Post by uwegeercken on 2010-05-05
I had the same problem that I cannot use agt-get in the terminal and it was definitely working before by setting the proxy and user authentication in System / Preferences / Network Proxy.

now this worked for me:

 I added:

Acquire::http::proxy "http://spi\ug010903:Lemmy4Me@proxy.swissport.aero:8080/";

to:

/etc/apt/apt.conf

rgds,

uwe

---

### Post by appier on 2010-05-06
> **uwegeercken said:**
> 

 I added:

Acquire::http::proxy "http://spi\ug010903:Lemmy4Me@proxy.swissport.aero:8080/";

to:

/etc/apt/apt.conf


This worked for me as well.  Thanks!

---

### Post by naaman on 2010-05-07
The /etc/apt/apt.conf fix worked for the sun-java6-jre package, however I also had to edit the following lines to /etc/wgetrc for the flashplugin-installer package:

```
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
https_proxy = http://user:pass@proxy.company.com:8080/
http_proxy = http://user:pass@proxy.company.com:8080/
ftp_proxy = http://user:pass@proxy.company.com:8080/

# If you do not want to use proxy at all, set this to off.
use_proxy = on
```

---

### Post by adbask on 2010-05-10
Hello everyone,

Can anybody please tell me where can I find the apt.conf?

I haven't seen it

I am using Ubuntu 8.04 hardy

There's no such a file as apt.conf

/etc/apt/apt.conf.d/

no file called apt.conf, where are  you getting this file from please?

I am having problems using my apt-get because before that I added a proxy, now I can't seem to get rid of it.

No matter what I do it's still looks for the proxy.
Is there anyone who has any idea on how to remove it, I didn't add it to any file
I used export and since then I can't shift it.

I wish people who give solutions to a particular problem on how to do something will also add a line on how to remove it.

Any help would be much appreciated 

Thank you

---

### Post by leona@simasima on 2010-05-12
The problem is the extra comma at the end of $no_proxy, as Krieg describes.

Lucid:
```

% echo $no_proxy
localhost,127.0.0.0/8,*.local,192.168.1.0/24,
```
Jaunty:
```

% echo $no_proxy
localhost,127.0.0.0/8,*.local,192.168.1.0/24
```

"sudo -i" initializes environmental variables with /etc/environment, thus $no_proxy is cleared and wget goes well.

Wget on Jaunty also fails to apply proxy settings when I add an extra comma at the very end of $no_proxy. It seems wget assumes that there is a wildcard (*) after the extra comma. I don't know whether this is a feature of wget or not.

---

### Post by Pureferret on 2010-05-17
I'm having a similar problem:
I've updated bashrc, and apt.conf to include the correct proxy settings with usernames and ports and all that jazz.

Done similar for the system>preferences>network proxy GUI, and the one in synaptic. the only thing I ahve working is firefox.

Can anyone help?

---

### Post by Ender985 on 2010-06-15
So, to recap everything I have done in Lucid 64bit for being able to correctly work behind a proxy (change 'your.proxy.addres' for your address, 'your_pac_file.pac' for yours if you use a .pac proxy, and 8081 for your port number):


1) System -> Preferences -> Network proxy

Manual proxy configuration, Use the same proxy for all protocols
HTTP proxy: [http://your.proxy.address/](http://your.proxy.address/) Port: 8081

Click "Apply System-Wide"

2) Synaptic Package Manager

Preferences -> Network tab
Manual config
HTTP proxy: your.proxy.address  Port: 8081
FTP proxy: your.proxy.address Port: 8081

3) gksu gedit ~/.bashrc &  # add, the following lines at the end:

```
https_proxy=http://your.proxy.address/your_pac_file.pac:8081
export https_proxy

http_proxy=http://your.proxy.address/your_pac_file.pac:8081
export http_proxy

ftp_proxy=http://your.proxy.address/your_pac_file.pac:8081
export ftp_proxy

export no_proxy=$(echo $no_proxy | sed 's/,$//')  
# This one last line is to "fix" the dreaded 'trailing comma' bug in the no_proxy environment variable 
```

4) gksu gedit /etc/wgetrc &  # Uncomment or add the lines
```

https_proxy = http://your.proxy.address:8081/
http_proxy = http://your.proxy.address:8081/
ftp_proxy  = http://your.proxy.address:8081/

use_proxy = on
```

5) gksu gedit /etc/apt/apt.conf &  # Add or modify the lines
```
Acquire::https::proxy "http://your.proxy.address:8081/";
Acquire::http::proxy "http://your.proxy.address:8081/";
Acquire::ftp::proxy "http://your.proxy.address:8081/";
```

Bonus) Firefox: Edit -> Preferences -> Advance -> Network -> Settings 

Manual proxy configuration, Use this proxy server for all protocols
HTTP Proxy: [http://your.proxy.address](http://your.proxy.address) Port: 8081

Appendix) And restart

And after doing this, I was finally able to get Synaptic to properly complete the 'flashplugin-installer' wget download and proceed with the installation! Easy huh? I still don't get if there is a 'Network proxy' setting with a button that says "Apply System Wide", the remaining 4 points still need to be applied in order for it to work properly.

---

### Post by karlvirgil on 2010-06-15
This work perfectly.  Thanks!

---

### Post by bodhi.zazen on 2010-06-15
> **Ender985 said:**
> 3) gksu gedit ~/.bashrc &  # add, the following lines at the end:

https_proxy=http://your.proxy.address/your_pac_file.pac:8081
export https_proxy

http_proxy=http://your.proxy.address/your_pac_file.pac:8081
export http_proxy

ftp_proxy=http://your.proxy.address/your_pac_file.pac:8081
export ftp_proxy

FYI: you can simplify those lines:

```
export https_proxy=http://your.proxy.address/your_pac_file.pac:8081

export http_proxy=http://your.proxy.address/your_pac_file.pac:8081

export ftp_proxy=http://your.proxy.address/your_pac_file.pac:8081
```

You can probably make those settings system wide by adding them to /etc/environment (rather then per user).

---

