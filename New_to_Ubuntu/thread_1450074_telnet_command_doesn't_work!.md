---
title: "telnet command doesn't work!"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by masterxunil on 2010-04-08
Hello everyone i am having some trouble with the configuration of my postfix.I follow the step by step configuration and installation .But once i type "telnet localhost 25" here is what i only get:

trying ::1...
connected to localhost.
Escape Charactere is '^]'.
_

and nothing else.please help me! i dont think i fail in the config.

Tks a lot !!

---

### Post by Agent ME on 2010-04-08
It looks like it connected and is working fine. What are you expecting? Try typing "help" and seeing if it responds.

---

### Post by gmargo on 2010-04-08
When you telnet to the SMTP port, you should see an string sent from the server, which starts with "220".  If you don't see the "220" then something is wrong.

```

$ telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 lucidbeta1 ESMTP Postfix (Ubuntu)

```If you then type a line that starts with "HELO", then it will respond with a "250" message.

```

HELO banana.org
250 lucidbeta1

```

---

