---
title: "trying to update banshee"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by herrnaphta on 2009-12-04
im trying to update banshee to the latest version via the website: [https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)  I'm stuck on step 4, tho, and I can't for the life of me find the 'apt line' to which it's referring.  i've tried 'deb            [B]ppa:banshee-team/ppa' but the 'add source' button doesn't become available.  what am i supposed to enter here?
[/B]

---

### Post by zkriesse on 2009-12-04
Ok, in your software sources menu go to "Other Software" Click "Add" in that type **ppa:banshee-team/ppa** click "Add Source" and then click close. When it prompts you to reload do so. After that if you've not installed Banshee do so by going to Applications -> Accessories -> Terminal. In the Terminal type, without quotes, "**sudo apt-get install Banshee" That should do it!**

---

### Post by herrnaphta on 2009-12-04
when i put **ppa:banshee-team/ppa **in, the 'add source' button remains greyed out, so i can't click it.  is there a way to add the ppa through the terminal that gets around this?

---

### Post by herrnaphta on 2009-12-04
Some more information:
The description above the box where I enter the APT line reads:
The APT line includes the type, location and components of a repository, for example  'deb [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 main'.

To unlock the button, it requires that three different 'words' be entered.  So the sample ''deb [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 main' unlocks the button, and so does gibberish like 'deb jg fj'.  But 'deb   ppa:banshee-team/ppa' is missing a term.

---

### Post by herrnaphta on 2009-12-04
still haven't figured this out.

---

### Post by avtolle on 2009-12-04
Add these lines to the software sources file (if you are using 9.10):

deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main

If you are using an earlier version of Ubuntu, click on the "Technical Details for this PPA" link that appears at:
[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa) 

then select the correct version from the drop down box, and copy/paste into Software Sorces as explained above. You may want to add the signing key as well, explanation at above launchpad link. Good luck.

---

### Post by herrnaphta on 2009-12-04
Thanks!  I got the PPAs added, but when i try to update banshee using synoptic, i get: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages](http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nothingspecial on 2009-12-04
open up a text editor

copy and paste this into it
```

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXWDEQEEAMoYQN5/6HptUWokWxGPNrJL8BtixSVpAjOMpNyzN27I6Ofl+5FWf+OidUpI
2brAq8uspnvCxdRU7nYNJjaEZU3lyS1R48SpeCXi4ynP5o4nOHv4wXnjTesszbimXLWfnOjN
G32rI+fMLuXderCU3ZMoHLqnhm/0o3JHVjwswkCLABEBAAG0HkxhdW5jaHBhZCBQUEEgZm9y
IEJhbnNoZWUgVGVhbYhGBBARAgAGBQJJeqdKAAoJEEF/tkJIIf4k20MAoISSdMjpHlPQgWmq
a+4hcuOhoCkFAJ9KabMOR6M/t9b1GidzRKvT+5IJx4i2BBMBAgAgBQJJdYMRAhsDBgsJCAcD
AgQVAggDBBYCAwECHgECF4AACgkQSHTTaG6AxrcH8gP/XXQHv1WTXfRSXvd4xykkLy+BEIZz
ImdTM8qyAoLtMsZFOKPEer1yfdB59AQXxnpm541YEn2hUmGhUgzz0XyTg+HCXQs8Go1AC4ie
7Mdl1uMnD144T6x+G/VVojXpJ4RswNS3r6ZVoVTxQm75EBoYqOwOByzh4oq1vE5VL6dNoqE=
=dWkD
-----END PGP PUBLIC KEY BLOCK-----
```

save it as key.txt

open up system > preferences > software sources and choose the import key or security or whatever it`s called - (sorry, not using ubuntu at the moment)

navigate to your saved key.txt file.
```

sudo apt-get update && sudo apt-get install banshee
```

---

### Post by nothingspecial on 2009-12-04
Update......

Just grabbed my wifes computu - as she calls it

You want the authentication tab in software sources. Choose the import key option.

---

### Post by herrnaphta on 2009-12-04
Spits out this:
```
Hit http://www.array.org jaunty Release.gpg
Ign http://www.array.org jaunty/main Translation-en_US                         
Ign http://www.statux.org jaunty Release.gpg                                   
Ign http://www.statux.org jaunty/main Translation-en_US                        
Hit http://www.array.org jaunty Release                                        
Ign http://www.statux.org jaunty Release                                       
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Ign http://www.statux.org jaunty/main Packages                                 
Hit http://packages.medibuntu.org jaunty Release                               
Ign http://www.statux.org jaunty/main Packages                                 
Hit http://www.array.org jaunty/main Packages                                  
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://packages.medibuntu.org jaunty/free Packages                         
Err http://www.statux.org jaunty/main Packages                                 
  404 Not Found
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://www.array.org jaunty/main Sources                                   
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://ppa.launchpad.net karmic/main Sources                               
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Ign http://repos.eeebuntu.org eb3 Release.gpg                                  
Ign http://repos.eeebuntu.org eb3/main Translation-en_US                       
Ign http://repos.eeebuntu.org eb3/non-free Translation-en_US                   
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Ign http://repos.eeebuntu.org eb3/contrib Translation-en_US                    
Get:1 http://repos.eeebuntu.org eb3 Release [1952B]
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://repos.eeebuntu.org eb3/main Packages
Hit http://us.archive.ubuntu.com jaunty Release
Ign http://repos.eeebuntu.org eb3/non-free Packages                 
Ign http://repos.eeebuntu.org eb3/contrib Packages
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://repos.eeebuntu.org eb3/main Packages
Hit http://repos.eeebuntu.org eb3/non-free Packages
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://repos.eeebuntu.org eb3/contrib Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 1B in 2s (0B/s)  
W: Failed to fetch http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by CaptainMark on 2009-12-04
> **herrnaphta said:**
>   But 'deb   ppa:banshee-team/ppa' is missing a term.
Since karmic, software sources doesnt seem to work the same, i used this line in software sources when i clean installed karmic and it added the normal [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) and also automaticaly added the key aswel.

And the repo thats not working is statux.org according to the message you gave, this isnt related to banshee so banshee should work fine, but whatever software you got from there probaly wont update

---

### Post by LuisGMarine on 2009-12-06
First Delete any previous ppa that you added for Ubuntu.  The problem is that you are trying to download from the karmic server, instead of the jaunty which is what you have.  So please before we start Follow this: :KS

Click on **System > Administration > Software Sources**

Using the tabs on the top, click on "**Other Software**."  Delete anything that says *[http://ppa.launchpad.net/banshe](http://ppa.launchpad.net/banshe) *

Once you do that click on Add and copy and past the following line into the dialogue box and hit "Add Source"
```
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main 

```

After you close that window, you can install banshee anyway you want now, either using Synaptics, Ubuntu Software Center, or command line.

I personally prefer using the Ubuntu Software Center located by going to **Applications > Ubuntu Software Center** then just type in banshee, select the arrow next to its name and install away.

Hope this helped.

---

### Post by herrnaphta on 2009-12-11
That did it!! Thank you for your help!!

---

### Post by LuisGMarine on 2009-12-11
> **herrnaphta said:**
> That did it!! Thank you for your help!!

Great!  Can you please mark this thread as solved by using the Thread Tools at the top?  Thanks and enjoy! :popcorn:

---

