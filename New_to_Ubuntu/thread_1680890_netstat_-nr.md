---
title: "netstat -nr"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by what-is-a-computer? on 2011-02-03
Can anyone tell me what this mumbo-jumbo means?  Thanks.



XXXXX@XXXXXX~$ gksudo netstat -nr
gksudo: invalid option -- 'n'
GKsu version 2.0.2

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
XXXXX@XXXXXX:~$

---

### Post by jdmcclung on 2011-02-03
You tried to run command: gksudo netstat -nr
program gksudo replied: gksudo: invalid option -- 'n'

It then lists the valid options for gksudo. If, as I believe, you intend the -nr to be options for netstat I suggest that you run just gksudo in the command line. It will then bring up a dialog box in which you can enter your command line: netstat -nr.

---

### Post by what-is-a-computer? on 2011-02-03
thanks

---

### Post by gmargo on 2011-02-03
Root privilege is not required to view the routing table.

---

### Post by Rubi1200 on 2011-02-03
Correct me if I am wrong, but you should use sudo to preface these commands.

gksudo is for graphical applications.

---

