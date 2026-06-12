---
title: "JDownloader Key"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by lhb1142 on 2010-06-10
):P Hello all. I recently downloaded the JDownloader program from here < [http://www.mediafire.com/?0ldht1g4zlv](http://www.mediafire.com/?0ldht1g4zlv) > and I installed it. It works perfectly.

But I'd like to have JDownloader in my repository. So I went to various sites which explained how to enter the requisite source into my Software Sources. Everything goes well (I have the proper URL < [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) lucid main > in place) UNTIL I try to obtain the key.

When I use the Terminal to install that repository, the key is supposed to be automatically obtained. It is not. Thus, I have tried to get the key myself.

Suffice it to say that I have tried this (with the results as shown):

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
gpg: requesting key 6A68F637 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

(This is the same error message I get when I try to get the key when I enter the commands to install the URL into my Software Sources.)

and I also tried this (also with results shown):

sudo apt-key adv --keyserver subkeys.pgp.net --recv-keys 6A68F637
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver subkeys.pgp.net --recv-keys 6A68F637
gpg: requesting key 6A68F637 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

When I go to the subkeys.pgp.net site, I can easily find the JDownloader key by searching for it; I get:

Search results for 'jdownloader'

Type bits/keyID     cr. time   exp time   key expir

pub  1024R/6A68F637 2010-04-13            

uid Launchpad JDownloader PPA
sig  sig3  6A68F637 2010-04-13 __________ __________ [selfsig]

and, when I click on the 6A68F637, I get:

Public Key Server -- Get ``0xd6b6db186a68f637 ''

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.1.1

mI0ES8SaRwEEAMqgLs42uul4IDuo6q1aiX1JaakPJ3NpOdJemnM7wM/vvzY8sGdzsNA0125g
scvbAt5xoX0N/nivQV84x/WdzT3xQMfEyJMw7NCKHzAOsNgTmMtdQrEoh1BScAgYZLH3fWmQ
+NtdRqTi5FLuWYsdhY0IUR7IYPy0AaoA6eSbZIrTABEBAAG0GUxhdW5jaHBhZCBKRG93bmxv
YWRlciBQUEGItgQTAQIAIAUCS8SaRwIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJENa2
2xhqaPY3rO8D/ixrXoZDnhwLQDnsQmg4ZsMMiaOsJ5I3sJX4P5BGGIk2TMfvJCoR+IT1L1Mr
KITSMJa+oj57lcvdqF9Ohj/Y8B8+Jzd3uWazdU76o1i357xnl6C2JFIYLztzoGVlMMaQPVpm
BU7klyuw7kXjRP4zIKdkBxliequOcp7P4RmliEqP
=oQPP
-----END PGP PUBLIC KEY BLOCK-----

As I evidently cannot directly connect to keyserver.ubuntu.com or subkeys.pgp.net in order to install this key (I have been trying for a week now!), is there some way I can MANUALLY install this key into my Software Sources Authentication? I would really appreciate step-by-step instructions.

Obviously this is not "urgent," as JDownloader works perfectly just as is (from my .deb download) but I would REALLY like to have it in my repository.

Thanks for any help.

Lawrence H. Bulk  :confused:

---

### Post by oldos2er on 2010-06-10
Save the text of the key, including the BEGIN and END BLOCK, to a file in your home folder called jdownloader.ppa.key, then run ```
sudo apt-key add jdownloader.ppa.key
```

Or open Software Sources, Authentication, Import Key File....

---

### Post by lhb1142 on 2010-06-10
> **oldos2er said:**
> Save the text of the key, including the BEGIN and END BLOCK, to a file in your home folder called jdownloader.ppa.key, then run ```
sudo apt-key add jdownloader.ppa.key
```

Or open Software Sources, Authentication, Import Key File....

The second method worked! Thanks Ann.

Lawrence :smile:

---

