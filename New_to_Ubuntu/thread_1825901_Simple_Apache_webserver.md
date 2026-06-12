---
title: "Simple Apache webserver"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Ac30nfir3 on 2011-08-15
Hello all!

I am attempting to setup a simple Apache webserver that can be accessed by anyone on the internet using the IP address of my server box. I am running **Ubuntu Server Edition 11.04** and have installed apache2 using apt-get.

I have a site enabled, but whenever I try to connect to it remotely (using SSH to access the box, since its not local) it says it cannot connect. I'm not 100% clear on how I have to set it up so that everyone can view it, but I have been reading about ServerName and similar commands.

ALSO, I have set my hostname to be (Example) servername.myisp.com but this did not help. Does anyone know where I can either find an absolute noob guide to setting up an apache web server, or anyone know what could be the problem?

---

### Post by alphacrucis2 on 2011-08-16
> **Ac30nfir3 said:**
> Hello all!

I am attempting to setup a simple Apache webserver that can be accessed by anyone on the internet using the IP address of my server box. I am running **Ubuntu Server Edition 11.04** and have installed apache2 using apt-get.

I have a site enabled, but whenever I try to connect to it remotely (using SSH to access the box, since its not local) it says it cannot connect. I'm not 100% clear on how I have to set it up so that everyone can view it, but I have been reading about ServerName and similar commands.

ALSO, I have set my hostname to be (Example) servername.myisp.com but this did not help. Does anyone know where I can either find an absolute noob guide to setting up an apache web server, or anyone know what could be the problem?

Does your ISP allocate you a static IP address? If not you can get around that by using something like dyndns. You will probably also need to set up port forwarding on your internet router if your apache server is running on a private RFC style address. I'm not sure what you are trying to do with ssh as apache serves up http and or https. For ssh you would need to install an ssh server such as openssh. Also be careful running a web server and making it accessible from the internet as this may be restricted by your ISP's terms of service.

---

### Post by Ac30nfir3 on 2011-08-16
> **alphacrucis2 said:**
> Does your ISP allocate you a static IP address? It does not. > **alphacrucis2 said:**
> If not you can get around that by using something like dyndns. You will probably also need to set up port forwarding on your internet router if your apache server is running on a private RFC style address. Im using dlinkddns.com, and the ports are forwarded. > **alphacrucis2 said:**
> I'm not sure what you are trying to do with ssh as apache serves up http and or https. For ssh you would need to install an ssh server such as openssh. I am using SSH to install apache set up the server, I know apache serves http... > **alphacrucis2 said:**
> Also be careful running a web server and making it accessible from the internet as this may be restricted by your ISP's terms of service. This is taken care of.

Thanks for the help.

---

