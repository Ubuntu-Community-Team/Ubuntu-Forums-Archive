---
title: "Is it possibly a password to check mail?"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by e.jejcic on 2011-07-11
As the title says I would like to have a password before checking my mail and after logged into Ubuntu. Is it possibly?. Thanks in advance from Eduardo.

---

### Post by Vaphell on 2011-07-11
what program do you use to check email? maybe there is some 'remember password' checkbox that can be ticked off.

---

### Post by e.jejcic on 2011-07-11
Thank you for the really fast response. I am using as my email clientThunderbird. I have three email accounts. I really don't know where the check box should be. Thanks from Eduardo.

---

### Post by ajgreeny on 2011-07-11
Go Edit -Preferences in T'Bird and on the **Security** section **Passwords** tab you can remove your saved passwords.  Just remember not to select to remember the password next time you use T'Bird.

---

### Post by godjil on 2011-07-11
...possibly, You recently changed Your login password, and You need to change the password in seahorse.

---

### Post by e.jejcic on 2011-07-11
Well, let's answer (in parts):
Mr. ajgreeny: I think that what you said is the passwords for retrieve mail from the servers. Is not what I ment.
The thing that I was asking is a password for reading the already downloaded mails  from the servers. I think that I was asking something that is not possibly; it is like  putting a password for any application I want to open (I guess). I will mark this thread as solved because my thinking is wrong (I guess).
Thank you for the input. Regards from Eduardo.

---

### Post by ajgreeny on 2011-07-11
This will depend on the protocol you use and the settings for that.

If you use pop3, it will download all messages in full, and they will be sitting in your thunderbird profile's mail folder, so can be read without password entry

If you use imap, you can choose to download either the complete content of messages or just the headers, I think.  If you choose just headers, not the body of messages to be downloaded, it will be necessary to connect to the mail servers at your ISP, or at gmail or yahoo etc etc, which will need a password each time in order to read messages, unless you have set the account to remember passwords.

I hope that is some help.  Apologies if I have still misunderstood what you mean.

---

### Post by Brandel Valico on 2011-07-11
I believe this is what you may be looking for. I don't use Thunderbird so I can't test it. So do so at your own risk.

> Open the Mozilla Thunderbird email program. Click "Tools" in the options bar at the top of the screen. Select "Options" in Windows, or "Preferences" in Mac OS X and Linux, from the drop-down menu. Open the "Advanced Options" panel.
Quote:
Select the "General" tab. Click on the "Config Editor" option. A list of preferences and a search bar are displayed.
Quote:
Double-click the "mail.password_protect_local_cache" preference to enable you to change the assigned value. Change the value to "True."
Quote:
Close the Mozilla Thunderbird email program to allow the program to refresh and for your changes to take effect.
Quote:
Reopen the Mozilla Thunderbird email program. Your password protection is now enabled for use. 

---

