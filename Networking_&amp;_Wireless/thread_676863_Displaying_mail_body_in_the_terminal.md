---
title: "Displaying mail body in the terminal"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by franestepona on 2008-01-24
Hi guys, I was looking for a program to retrieve new mail from my gmail account and display the subject or the body of the message. The reason I want this is because I made a little script that sends a text file to my phone via bluetooth, so it could be great if I could send the text file with the body of the message when it arrives. I have tried getmail and fetchmail, but they are a pain to configure and although they get new messages from the server I cant get them to display the contents on the terminal. So the script looks like this:

```
#!/bin/bash
echo [(here is where i need the comand to display the message body and header)] > "/home/fran/mail.txt"
gnome-obex-send --dest=00:1A:16:1B:6C:54 '/home/fran/mail.txt']
```

Was it clear? Any suggestions?

---

