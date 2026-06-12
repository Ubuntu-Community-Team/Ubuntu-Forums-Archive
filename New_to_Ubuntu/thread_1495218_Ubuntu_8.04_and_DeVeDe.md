---
title: "Ubuntu 8.04 and DeVeDe"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-05-27
Hello. When I first started using Ubuntu, I used version 9.10. Of all the programs, I came to like the program "DeVeDe" a lot, but later I downgraded to version 8.04 for driver reasons.
After installing DeVeDe on my Ubuntu 8.04 installation, I've noticed that it looks different and is missing the "Adjust disc usage" button.
My first thought was that it was an older version, so I googled "DeVeDe" and downloaded the .deb installer for the latest version.
After running the .deb, it gives me the following:
Error: Dependency is not satisfied: python-gtk2

So I opened the terminal, and ran the command "sudo apt-get install python-gtk2" so I could install the package and satisfy the dependency, but the problem is I recieve the message "python-gtk2 is already the newest version."
If I have the right python, why is it that the installer says the dependency is not satisfied? I'd prefer to install DeVeDe this way, because using "sudo apt-get install DeVeDe" or using add/remove always gives me an older version.
Does anyone know how I could go about doing so? Thanks in advanced, any help is appreciated.

---

### Post by Stigmata13 on 2010-05-27
Bump :)

---

### Post by halitech on 2010-05-27
its considered proper etitiquet to wait 24 hours before bumping a thread :)

If the .deb version is asking for a newer version of python-gtk then what you have as a requirement to installing the .deb version then you need to get the newer version and probably compile it from source. 

Ubuntu is designed to work with the versions that are available in each releases repo and if you need something newer, you have to find a backports repo (PPA) if available or compile it yourself.

---

