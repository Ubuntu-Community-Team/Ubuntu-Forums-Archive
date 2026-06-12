---
title: "How to access ubuntu server shared disk"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by anewguy on 2009-01-27
Ok, I know this makes me look like a complete idiot - but I don't mind as long as I can get some guidance! :)

I have an old box running Ubuntu 8.10 server edition and set up as a very simple server for sharing a disk according to instructions I found on the net.  I am able to access it from Windows with no problem, but as dumb as it sounds I have no clue how to do it from Ubuntu desktop edition.  The workgroup is dwe-wrk-group, but beyond that I don't know what to do on the desktop side.

Any help for an old idiot would be greatly appreciated!

Dave :)

EDIT:  I should mention the server is using Samba, if that makes any difference.

---

### Post by Ahadiel on 2009-01-27
If you go to "Places" ==> "Network", it should show up.

---

### Post by XanTrax on 2009-01-27
Are you running 8.10 or 8.04?

Suggested on 8.04 to run
```
sudo apt-get install openssh-server openssh-client
```

and on 8.10
```
sudo apt-get install ssh
```

After you run those commands, on the server type
```
ps -A | grep -i sshd
```

to ensure the SSH daemon is running.  Then
```
sudo netstat --tcp --program -an | grep -i listen
```

to ensure that SSH daemon is listening for connections on port 22.  If you get those results then you can be sure that SSH server daemon is running and actively listening for connections.

Make sure you create a user to connect on, for example:

```

sudo adduser fileaccess
Adding user `fileaccess' ...
Adding new group `fileaccess' (1001) ...
Enter new UNIX password: test
Retype new UNIX password: test

```


Fill in corresponding information.  In this example, we used fileaccess as the username and for the password we set it to test

Now, on the computer where you want to access the server:

Click "places" at the top then click "connect to server" and fill in the corresponding information.  Service type is SSH, IP is the server IP, username is fileaccess, port is 22, and folder is /home/fileaccess.  Once connected, you will be prompted for the password.  Type in whatever password you set, following suit with our example I would type test.

---

### Post by anewguy on 2009-01-27
Thanks very much to both of you - everything working great!

Dave :)

---

