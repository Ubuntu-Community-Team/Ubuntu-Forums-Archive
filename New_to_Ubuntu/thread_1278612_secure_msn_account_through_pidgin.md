---
title: "secure msn account through pidgin"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by sundol on 2009-09-29
I've heard that msn message is sent in a clear text form through net.
I use msn account in pidgin.

1. Message through MSN account in pidgin is encrypted by default?

2. If not, how to encrypt my message through msn account of pidgin?

3. Is it possible to chat with msn users who do not encrypt their message?

4. Is it possible to know if chatting partner use encryption? (simply encrypted or not without knowing the full message).

5. If chatting partner's message (msn on windows) are unencrypted and I want secure chatting, what is the easiest way for chatting partners to make theirs encrypted (except shifting to Ubuntu. :) )?

Thank you. :)

---

### Post by jonobr on 2009-09-29
Hello

Some answers for you,
Your correct what you say, it is unencrypted.
To encrypt the MSN traffic there used to be a package to encrypt both ends of a session, it was called simp server 

The code is no longer supported by the company but you can get beta code 
[here]("http://www.secway.fr/us/products/simpserver/download.php") 

theres a few howtos on the forums that will walk you through setting it up.

You need the other person running the same software.

AS for detecting what the other end is doing, Im not sure on that.

---

### Post by dearingj on 2009-09-29
You can use encryption without installing simp server.

> **sundol said:**
> I've heard that msn message is sent in a clear text form through net.
I use msn account in pidgin.

1. Message through MSN account in pidgin is encrypted by default? 

No, I don't believe these messages are encrypted by default.

> **sundol said:**
> 
2. If not, how to encrypt my message through msn account of pidgin?

Install the pidgin encryption plugin (on Ubuntu run: "sudo apt-get install pidgin-encryption", otherwise go to [http://pidgin-encrypt.sourceforge.net/](http://pidgin-encrypt.sourceforge.net/) and follow the instructions there). Then restart Pidgin and, in the Buddy List window, click on Tools->Plugins. Scroll down the plugin list until you find Pidgin-Encryption. Check the box next to it.

> **sundol said:**
> 
3. Is it possible to chat with msn users who do not encrypt their message?

Yes, it is.

> **sundol said:**
> 
4. Is it possible to know if chatting partner use encryption? (simply encrypted or not without knowing the full message).
Yes, that is one of the options when you configure the encryption plugin.

> **sundol said:**
> 
5. If chatting partner's message (msn on windows) are unencrypted and I want secure chatting, what is the easiest way for chatting partners to make theirs encrypted (except shifting to Ubuntu. :) )?

Get them to install Pidgin and the encryption plugin. Pidgin works with Windows.

---

### Post by major.stubble on 2009-10-27
> **dearingj said:**
> 
[quote=sundol]*3. Is it possible to chat with msn users who do not encrypt their message?*
Yes, it is.
[/quote]

A small correction here.

You will still be able to chat with MSN users who do not encrypt their messages, **but your messages will not be encrypted.**  The encryption plugin will determine that the target user is not using any plugin capable of decrypting your message, and (when configured correctly) will (re)send the message in plain text.

---

