---
title: "guess the cronjob problem"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by navaneethan on 2010-12-19
I need to execute the cron jobs i have checked more times the path of each in the following cron jobs command 


```
#upgrade_remainder
#00 01 * * * /home/ubuntu/hirelex/peoplelex/scripts/upgrade_reminder.sh 1>> /home/ubuntu/cronlogs/upgrade_reminder_out.log 2>> /home/ubuntu/cronlogs/upgrade_reminder_\
err.log

#execute_recruiter_contact_request
50 19 * * * /home/ubuntu/hirelex/peoplelex/scripts/execute_recruiter_contact_request.sh 1>> /home/ubuntu/cronlogs/execute_recruiter_contact_request_out.log 2>> /home/\
ubuntu/cronlogs/execute_recruiter_contact_request_err.log

50 19 * * * /home/ubuntu/hirelex/peoplelex/scripts/time.sh 1>> /home/ubuntu/cronlogs/time_out.log 2>> /home/ubuntu/cronlogs/time_err.log
```

but
the log file wasn't created ;may i know the reasons that is why the log files r not created 

could you guess this error?

---

### Post by CharlesA on 2010-12-19
Is your home directory encrypted?

---

### Post by gmargo on 2010-12-19
Permissions?

Make sure you have a Mail Transfer Agent, such as **postfix**, installed, so that cron can email you any errors.

---

### Post by navaneethan on 2010-12-20
yeah permission is done already

---

### Post by navaneethan on 2010-12-20
sorry i am not getting you plz tell little clear

---

### Post by idi0tf0wl on 2010-12-20
> **navaneethan said:**
> I need to execute the cron jobs i have checked more times the path of each in the following cron jobs command 


```

... upgrade_reminder.sh 1>> ...
... upgrade_reminder_out.log 2>> ...

```
but
the log file wasn't created ;may i know the reasons that is why the log files r not created 

could you guess this error?

Is this a copy/paste? Because if it is, you need to wrap anything with spaces in quotes. Or rename these things to 'upgrade_reminder1.sh' or so.

---

### Post by CharlesA on 2010-12-20
> **idi0tf0wl said:**
> Is this a copy/paste? Because if it is, you need to wrap anything with spaces in quotes. Or rename these things to 'upgrade_reminder1.sh' or so.

There are no spaces in the filenames. The way it's written is fine as is.

@OP: The only crontab entry that looks strange is this one:

```
50 19 * * * /home/ubuntu/hirelex/peoplelex/scripts/execute_recruiter_contact_request.sh 1>> /home/ubuntu/cronlogs/execute_recruiter_contact_request_out.log 2>> /home/[COLOR="Red"]\[/COLOR]
ubuntu/cronlogs/execute_recruiter_contact_request_err.log

```

Is there a reason for an escape character in the path, or is it a typo?

---

### Post by Toz on 2010-12-20
One other thing, this job is set to go off once a day at 8:50pm. Have you tested it at 8:50pm? You might try in your crontab * * * * * for testing purposes as this will set it off every minute.

---

### Post by bluefrog on 2010-12-20
is the task running at all?

if not use sh in front of the script path.

50 19 * * * sh /home/ub...

---

### Post by CharlesA on 2010-12-20
> **bluefrog said:**
> is the task running at all?

if not use sh in front of the script path.

50 19 * * * sh /home/ub...

You don't need sh or bash or anything if the shell script has a shebang at the top : #!/path/to/shell

---

### Post by seawolf167 on 2010-12-20
Just in case anyone else is having problems with their logs being logged in 10.04 or later (I know this doesn't apply to OP since he is 8.04), the cron logs moved from /var/log/cron.log to /var/log/syslog

(i.e. greping a cron log in 10.04 is something like: "cat /var/log/syslog | grep -i cronsearchtext" vs. "cat /var/log/cron.log | grep -i cronsearchtext"

To have the cron logs created in /var/log/cron.log instead, you'll need to edit /etc/rsyslog.d/50-default and remove the comment tag in front of the line "cron.* /var/log/cron.log".

This will enable writing of the cron logs to /var/log/cron.log vs. /var/log/syslog

---

### Post by navaneethan on 2010-12-21
just i typed that space character friend in the path

---

