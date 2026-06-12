---
title: "Hacking Skype Password"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by suomalainen on 2011-02-02
Ubunteros,

Would somebody please explain to me the following. If I were to cut & paste a portion of a Skype chat history into the body of an email and send it to the person requesting it, whether private information is also being forwarded that would enable the requester to determine my Skype password?


Thank you.

---

### Post by lisati on 2011-02-02
Unlikely. AFAIK passwords aren't stored in the chat history.

---

### Post by suomalainen on 2011-02-02
I'd like to be 100% certain?

Also, is there enough information being given that my Skype chat history could be hacked?

---

### Post by 3rdalbum on 2011-02-02
> **suomalainen said:**
> I'd like to be 100% certain?

When you use the "Copy" or "Cut" functions of a program, it stores (temporarily) only the text/object that was selected. It does not "copy" or "cut" any information that was not selected.

But hey, don't take my word for it. Go to your chat history and copy some text from it, and then paste it into a word processor. Does your password get pasted as well? If not, then your password will not reach the clipboard.

> Also, is there enough information being given that my Skype chat history could be hacked?

No, not a chance. There's no way of asking the Skype server "Hey, I have part of a chat transcript, can you send the rest of the transcript here". There's no legitimate use for this function, and it would represent an enormous breach of security, so the Skype developers would not have implemented it.

---

### Post by suomalainen on 2011-02-02
3rdalbum,

Thank you very much for your detailed response! On the surface what you say makes sense. But because I'm not a developer I really don't understand the fundamentals that you may know.

One thing I am wondering about is why Skype does not allow you to download your chat history. In my case it has to be done manually by cut & paste.

Thanks again for your support.

---

### Post by mastablasta on 2011-02-02
> **suomalainen said:**
>  
One thing I am wondering about is why Skype does not allow you to download your chat history. In my case it has to be done manually by cut & paste.
 
 
that would be a good question for the Skype support.  ;)

---

### Post by robsoles on 2011-02-02
It doesn't take rocket science to see that you 'copy' text from one window and 'paste' it in another window and it is just text.

If your mail client supports viewing the source of the email you are constructing then you can check it out before you send it and either BCC or flatout email yourself and see what gets added to the source by your client and mail server on it's journey by checking out it headers and source again when it arrives  - everything the recipient could possibly find or see is on display if you view the headers and the source code of the email.

(Just tried following in the Skype (Beta) Version 2.1.0.81), latest I can find in my 10.10 laptop's repository, and it failed flat out - tried it in a WinXP VM and the message didn't go to my friend but it didn't open Chrome with our chat history either)

In Skype message window, of the conversation you want to 'save',  type
```
/htmlhistory
``` and send it, try it on 'Skype Test Call' or someone you trust to be 'ok' with it if they find you trying the command and google it - if your version of Skype is 'good' then it will open a page in your browser and you can 'file'->'save' that from the browser.

---

