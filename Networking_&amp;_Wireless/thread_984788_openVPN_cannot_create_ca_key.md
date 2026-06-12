---
title: "openVPN cannot create ca key"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by steve_d on 2008-11-17
---------------------------------------------------------------------------
EDIT: I MUST BE BLIND, THE ANSWER IS ALREADY ON THIS SITE IN THIS THREAD:
[http://ubuntuforums.org/showthread.php?t=801135](http://ubuntuforums.org/showthread.php?t=801135) Post#5
---------------------------------------------------------------------------
I know openvpn info here is sparse at best, but if anyone has gone through the install I'm having some issues when generating a key.

I'm following the openvpn howto on this page [http://openvpn.net/index.php/documentation/howto.html#pki]("http://openvpn.net/index.php/documentation/howto.html#pki"). I've edited the vars file, then try to run the ```
./vars
``` and it gives me a warning "NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/2.0/keys" which I assume is normal, I then try to run the second command ```
sudo ./clean-all
``` for which I get this response: "Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration." So at this point I'm assuming theres an issue, because when I look at the script it says 'else' and then print the above message, so its not executing the command I'd like:

```

#!/bin/bash

# Initialize the $KEY_DIR directory.
# Note that this script does a
# rm -rf on $KEY_DIR so be careful!

if [ "$KEY_DIR" ]; then
    rm -rf "$KEY_DIR"
    mkdir "$KEY_DIR" && \
	chmod go-rwx "$KEY_DIR" && \
	touch "$KEY_DIR/index.txt" && \
	echo 01 >"$KEY_DIR/serial"
else
    echo 'Please source the vars script first (i.e. "source ./vars")'
    echo 'Make sure you have edited it to reflect your configuration.'
fi

```

I then try to run the last command anyways ```
sudo ./build-ca
``` which returns " Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys."

Anyone understand whats going on here?

---

