---
title: "Testing server vulnerbility for DDOS attacks"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Pithikos on 2010-12-10
I saw the LOIC thread that someone opened and got closed and understand that in that context the whole thing might had some illegal "texture".

Anyhow I wanted to test my server to see how vulnerable it is to DDOS attacks or other arbitrary attacks. Is there any other tool than LOIC for such a task? I don't like the fact that LOIC is written in C# and would therefore prefer a solution in a native linux language. Command line programs are ok but then I would like some neat explanation of each thingy, otherwise GUI is preferable.
I have some basic background in linux and computers/computer networks but nothing practical.

And to clarify once more: this is a testing to my own server and not some illegal act.

---

### Post by Pithikos on 2010-12-10
Well solved. Found a nice python script to do the job. You can find the script here: [http://www.mediafire.com/?5ddku7eub27rc9f](http://www.mediafire.com/?5ddku7eub27rc9f)

There are instructions in the zip file but what you practically are doing is extracting the *.py file and running it from command line like this:
```

python *.py ihatemytestingserver.com 80 15

```Where *.py should point to the script file. 80 stands for the port number(80 is standard for HTTP) and 15 is the number of threads(not sure what it means)

---

### Post by cariboo on 2010-12-10
Keep in mind that it is not recommended that you install packages/programs from untrusted sources. The code has not been reviewed, and it could contain malicious code. With that, this thread is closed.

---

