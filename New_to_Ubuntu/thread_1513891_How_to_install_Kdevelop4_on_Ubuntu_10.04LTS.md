---
title: "How to install Kdevelop4 on Ubuntu 10.04LTS"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by tonwib on 2010-06-20
Hi Group!

I am trying to install Kdevelop4 on my computer. Operating system used is: Ubuntu 10.04LTS.

I used these commands: 
"sudo apt-get kdevelop" (no result)
"sudo apt-get kdevelop4" (no result)
"sudo apt-get kdevelop3" (no result)

Also the Synaptic Package Manager didn't solve the problem. It cannot seem to find the program.

Now I've downloaded Kdevelop4 from [www.kdevelop.org]("http://www.kdevelop.org") and I am trying to install it, but there seems to be a lot of files missing. Cmake wants me to set a variable name. In the manual there is nothing to be found on how to set this variable name. So, I'm stuck again.

Can you direct me to a complete manual or tell me how to do a complete installation?

Thanks in advance.

Ton

---

### Post by tonwib on 2010-06-21
Anyone has an answer to my question, above? 

Thx,

Ton

---

### Post by mintyhippo on 2010-07-06
If the version does not matter to you, then just install it through the online repo. You may have to go to the kdevelop website and manually add the repo to your sources list if it is not showing up. If so, then there will be instructions on how to do this on their site.

---

### Post by ankspo71 on 2010-07-06
Hi,
Here is a link that shows kdevelop is now in Lucid Backports (Unsupported Updates)
[http://www.kubuntu.org/news/kdevelop-4](http://www.kubuntu.org/news/kdevelop-4)

Go to System > Administration > Software Sources.
enter password if asked.
When software sources opens, click on the "updates" tab.
put a checkmark by lucid-backports (unsupported updates) (words might be slightly different because I use Kubuntu)
Click on the close button
Now it will ask you to reload the repositories, so reload it by clicking on the reload button.
Then close the software sources window.

Now you can search for it in Synaptic Package Manager.
Hope that helps.

---

### Post by manganganath on 2010-10-01
Thank you. This really helps.

---

