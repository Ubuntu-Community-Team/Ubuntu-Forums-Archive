---
title: "Evolution and Outlook Web Access"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by DSn0wMan on 2010-07-26
This has worked well for me in the past, but there seems to be something totally broken in this version, or I am missing something really obvious

I have tried all the ways I can thing of. And none of them connect to the server, but I can easily connect through a web browser.

The specific error is...

"Could not configure Exchange account because an unknown error occurred. Check the URL, username, and password, and try again"

If I put the wrong password I get "Make sure the username and password are correct and try again".

If I run with debug from the terminal I see these errors

(evolution:14057): e-data-server-ui-WARNING **: Unable to find password(s) in keyring (Keyring reports: No matching results)

(evolution:14057): e-utils-WARNING **: No parent set, or default parent available for error dialog
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'

I tried entering all of the following without being able to connect.

domain\username
https://webmail.<company>.com


domain\username
https://webmail.<company>.com/exchange

domain\username
https://webmail.<company>.com/owa

domain\username
https://<server ip address>/

domain\username
https://<server ip address>/exchange

domain\username
https://<server ip address>/owa

---

### Post by DSn0wMan on 2010-07-26
Forgot to mention that its an outlook 2007 server I am connecting to if that makes a difference.

---

### Post by leveillerems on 2011-05-24
I believe that Microsoft block out external access to web outlook..:(:???:

---

