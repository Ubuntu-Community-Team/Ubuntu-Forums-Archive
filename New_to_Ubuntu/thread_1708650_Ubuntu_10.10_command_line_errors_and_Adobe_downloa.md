---
title: "Ubuntu 10.10 command line errors and Adobe download errors"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by wamdue child on 2011-03-16
Hi,

I'm totally new to Ubuntu and I want to move away from Windows but I've loaded 10.10 netbook on to my netbook and I'm having some very frustrating problems.

1. I downloaded Xampp 1.7.1 and went to my command terminal to follow the installation instructions. Xampp says at the command line type in su. Then it says type in tar xvfz xampp-linux-1.7.1.tar.gz -C /opt.

Now before I go any further I encounter a problem. The command line doesn't seem to recognise su or sudo or tar xvfz xampp-linux-1.7.1.tar.gz -C /opt.

It asks for my username and password so I put it in. Then I try su again and it says command failure or authentication failure. I'm asked for my login again and it again asks for my password. I enter them and try again and if I try su or sudu, the long tar command and even just tar I'm sent around in circles. So I go back to my username and password and then I try all the commands I have again. It either says the same thing or else something like command not recognised. 

No combination of entries gets me anywhere and I eventually just keep getting asked for my password. It's driving me absolutely crazy. I installed a root because it's the only thing that worked but I'm not sure if that's advisable. Either way I only met the same problems once the root installed.

Am I missing something fundamental?

2. My other problem is I try to download Adobe Flash to view a Youtube tutorial on command lines and it gets nowhere. I download the Adobe Installer from the repository and then try to download Flash Player -  I get a box saying do I want to trust this source. I click yes, and the button flashes so I know Ubuntu recognises that I've clicked it and I wait but NOTHING HAPPENS, not even a status bar, absolutely nothing! I thought Ubuntu was supposed to "just work". Well it doesn't for me and I really don't think I'm doing something particularly stupid.


ANY IDEAS ANYONE? ALL HELP VERY MUCH APPRECIATED!

---

### Post by rosencrantz on 2011-03-16
sudo tar -xvfz xampp-linux-1.7.1.tar.gz -C /opt
should prompt you only for your password. Just 'su' tries to change to the root account, which isn't active on Ubuntu.
On second thought, why not just get apache, php and mysql via package management? Much better integration and easier to get rid of:
sudo apt-get install apache2 php5 mysql-server
To get flash working, get it from the restricted formats repositories: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) or [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Cheers, rosencrantz

---

### Post by wamdue child on 2011-03-30
Many thanks Rosencrantz!
 
Sorry for the delay in replying to you. I've been so busy I haven't even got round to doing as you suggest but I'm sure it will work. Thanks a million!

---

