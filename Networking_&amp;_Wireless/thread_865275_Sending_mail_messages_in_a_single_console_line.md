---
title: "Sending mail messages in a single console line"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by glauco.b on 2008-07-20
Hello folks!

I'm sorry to bother you with these old-style issues, but I really need this.

Is there a way to send an e-mail message from the console?

I mean something like this:

> some_command <subject> <from> <to> <smtp_server> <username> <password>

I tried mail, mailx, nail, mutt, but I can't figure out how to specify the SMTP server options from the command line

any help will be apreciated

---

### Post by decoherence on 2008-07-20
Hi there. I set up something like this for work a while ago, unfortunately I'm not there now. If I recall correctly I used esmtp as the mail transfer agent and sendmail (not sure if it was really sendmail) to send the mail. I was able to send mail with a one-liner.

If you haven't worked it out or got a better response by monday, bump the thread and I'll see if I can dig up specifics.

---

### Post by glauco.b on 2008-07-20
OK, I ended up with a python script, found somewhere on the net

I post it here for future use

```

import smtplib
from email.MIMEMultipart import MIMEMultipart
from email.MIMEBase import MIMEBase
from email.MIMEText import MIMEText
from email.Utils import COMMASPACE, formatdate
from email import Encoders
import os

def sendMail(to, subject, text, files=[],server="localhost"):
    assert type(to)==list
    assert type(files)==list
    fro = "Expediteur <expediteur@mail.com>"

    msg = MIMEMultipart()
    msg['From'] = fro
    msg['To'] = COMMASPACE.join(to)
    msg['Date'] = formatdate(localtime=True)
    msg['Subject'] = subject

    msg.attach( MIMEText(text) )

    for file in files:
        part = MIMEBase('application', "octet-stream")
        part.set_payload( open(file,"rb").read() )
        Encoders.encode_base64(part)
        part.add_header('Content-Disposition', 'attachment; filename="%s"'
                       % os.path.basename(file))
        msg.attach(part)

    smtp = smtplib.SMTP(server)
    smtp.login("username","password") //not needed if SMTP server is open
    smtp.sendmail(fro, to, msg.as_string() )
    smtp.close()


sendMail(
        ["destination@dest.kio"],
        "hello","cheers",
        ["photo.jpg","memo.sxw"]
    )



```

cheers

---

### Post by decoherence on 2008-07-21
cool script. thanks for posting your results!

---

