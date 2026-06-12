---
title: "Please help me with PPTP!"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by castironpants on 2008-02-05
I swear, lack of internet is giving me the shakes. I'm currently writing this on a public computer while I'm studying abroad in Ireland. The university has this VPN client that I can't connect to. I get a signal, and an IP address, but I can't seem to route it. I've installed both the pptp nm-applet thing, and I do see VPN connections under the menu, and I also have pptpconfig, but nothing seems to work. I was told that I have to do it from command-line, or otherwise get some sort of script to do it. Can anyone give me a hand?

---

### Post by manzoor on 2008-02-05
from where did you downloaded pptpconfigg for Ubuntu ? im also having problems

---

### Post by joebeasley on 2008-02-05
pptpconfig is broken in gutsy.  Follow the manual instructions at [http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand).

---

### Post by manzoor on 2008-02-06
i cannot do the third step in the configuration

create or add lines to the /etc/ppp/chap-secrets file, which holds usernames and passwords:

$DOMAIN\\$USERNAME PPTP $PASSWORD *

cannot open chaps-secrets file

 help please

and do we also have to replace "$" or just the PASSWORd

for example if my password is gutsy

do I have to write "$gusty" or "gutsy" (without quotes) ??

---

### Post by joebeasley on 2008-02-06
create the file chap-secrets. sudo vi /etc/ppp/chap-secrets

# client        server                       secret                  IP addresses
*       <space here>       serverip_or_name  <space here>         your_password   <space here>     *

---

### Post by manzoor on 2008-02-06
sudo vi /etc/ppp/chap-secrets

# client server secret IP addresses
* manzoor gutsy *

i have to type this right

right ? manzoor is my username and gutsy is password

---

### Post by manzoor on 2008-02-06
how to create a /etc/ppp/peers/$TUNNEL file:

---

### Post by joebeasley on 2008-02-06
Yes that is correct.  The $Tunnel can be any name you choose. I named mine work.  ($tunnel is a name made up by you.

---

### Post by manzoor on 2008-02-06
how to create a /etc/ppp/peers/$TUNNEL file:


how ?

start the tunnel using the pon command:

pon $TUNNEL

and do I have to enter the pon $TUNNEL command at the terminal ?

---

### Post by manzoor on 2008-02-06
[B]to have the tunnel started on system boot:

    * for Debian Sarge, edit the /etc/network/interfaces file, and add this section:

      auto tunnel
      iface tunnel inet ppp
              provider $TUNNEL

    * for Debian Woody, edit the /etc/ppp/no_ppp_on_boot file, remove the first line comment, and change the word provider to the name of your tunnel, so that it looks like this:

      #!/bin/sh
      ...
      $PPPD call $TUNNEL

      (The line ... means the other lines in the file, it doesn't mean a line with three dots.)

      Then rename the no_ppp_on_boot file and make it executable:

      # mv /etc/ppp/no_ppp_on_boot /etc/ppp/ppp_on_boot
      # chmod +x /etc/ppp/ppp_on_boot

Every time your computer starts, the tunnel will be started automatically.[/B]

which one should I follow for UBUNTU ?

---

### Post by joebeasley on 2008-02-06
The file you create in the peers directory is a filename chosen by you.  They use $tunnel as a place holder.  

So say you created a file called work in the peers directory.  To start the connection you would type "pon work" to connect.  "poff work" will disconnect it. 

You don't need the options to start the tunnel at boot.

---

### Post by manzoor on 2008-02-06
so how to create the file

---

### Post by joebeasley on 2008-02-06
Use you favorite editor. vi or nano.

---

### Post by manzoor on 2008-02-06
thanks im going to boog ubuntu now and see if it works

---

### Post by manzoor on 2008-02-06
when I typed 

sudo vi /etc/ppp/chaps-secrets

the file opened up in the terminal but I couldnt type any thing there

i also tried sudo nano /etc/ppp/chaps-secrets

in nano i was able to type the username and passwords

but how can I save it ?

---

### Post by castironpants on 2008-02-06
Well, I like sudo gedit. Then you can save it easy.

---

