---
title: "Need help installing alien"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by nebu on 2010-06-11
Hey,

Alien is a middleware agent for the WLCG grid...

I am following the instructions to install alien from here [http://alien2.cern.ch/](http://alien2.cern.ch/).... 

however... when in run **./Install.sh -new_vo**

i get this weird error which i cant seem to figure out....

```

VAMOS BIEN
Parsing the arguments -new_vo
Doing the NEW_VO 
Checking if the certificate is ok
/home/subho/.alien/globus/usercert.pem: OK
Test  1 user_basic/001-use..........................................(4    seconds)ok
Test  2 new_vo/02-classads..........................................(0    seconds)ok
Test  3 new_vo/03-createorgldap.....................................(4    seconds)ok
Test  4 new_vo/04-createorgdb.......................................(33   seconds)ok
Test  5 new_vo/05-rotate............................................(22   seconds)ok
Test  6 new_vo/06-createorgservices.................................(101  seconds)failed


Error doing new_vo/06-createorgservices 6
Output
1..1
# Running under perl version 5.008008 for linux
# Current time local: Fri Jun 11 17:25:30 2010
# Current time GMT:   Fri Jun 11 15:25:30 2010
# Using Test.pm version 1.25

ERROR: Proxy file doesn't exist or has bad permissions
       globus_sysconfig: Could not find a valid proxy certificate file location
globus_sysconfig: Error with key filename
globus_sysconfig: File does not exist: /tmp/x509up_u1000 is not a valid file

Use -debug for further information.
This script will configure the startup of the AliEn Services for a new AliEn Organisation

If you run this script as the user 'subho', all the services will run under that identity.
Is that really what you want? (Y/N) [N]:Please, enter the following information:
Organisation name [ALICE]:LDAP host and DN (leave it empty if you want to look for it in the alien ldap server) []:Do you want to enable MonaLisa ? [Y/n] [Y]:On what host it should run?  [Mindstorm.cern.ch]:What will be the name of the service?  [Mindstorm]:This machine has to run: Proxy IS Authen Server Logger Broker TransferManager TransferBroker TransferOptimizer JobOptimizer CatalogueOptimizer PackManMaster MessagesMaster SEManager JobInfoManager MonaLisa
Is this right? [Y]:Create an environment file in user directory (Y/N) [Y]:To install the proxy you need the mysql admin password to Mindstorm.cern.ch:3307
Enter admin password for mysql on Mindstorm.cern.ch:3307 []:stty: standard input: Invalid argument

stty: standard input: Invalid argument
To install the authen you need the ldap root password to Mindstorm:8389
Enter admin password for Mindstorm:8389 []:stty: standard input: Invalid argument

stty: standard input: Invalid argument
Enter root dn for Mindstorm:8389 [cn=Manager,dc=cern,dc=ch]:Do you want to run Authen as 'root' (necessary if you use shadow passwords)?[Y/N] [Y]:Log directory [/home/subho/AliEn/log]:Directory for temporary files [/tmp/AliEn/tmp]:Directory for cache [/tmp/AliEn/cache]:Setting up the services with the following information
********************************************

Organisation name:     Mindstorm
Administrator password: ******
Username:              subho
Environment file:      Y
Services to start:     Proxy IS Authen Server Logger Broker TransferManager TransferBroker TransferOptimizer JobOptimizer CatalogueOptimizer PackManMaster MessagesMaster SEManager JobInfoManager MonaLisa
Shadow passwor:        N
********************************************
Proceed with creation [Y]:Trying to connect to the catalogue...
Creating Environemnt file...					ok
Connecting to ldap server on Mindstorm:8389...	ok
Creating ssh keys for subho...				ok
Writing private key to disc...					ok
Writing public key to disc...					ok
Adding the user 'subho' to ldap...			ok
Giving admin privileges to subho...			ok
Adding MonaLisa to LDAP [ou=MonaLisa,ou=Services,ou=CERN,ou=Sites,o=Mindstorm,dc=cern,dc=ch] ...			ou=Services,ou=CERN,ou=Sites,o=mindstorm,dc=cern,dc=ch: No such object at /home/subho/alien.v2-18.54/scripts/CreateOrgServices.pl line 523
Searching for Mindstorm:8389/o=Mindstorm,dc=cern,dc=ch 
ok
Copying the directory to /root/.alien...ok
Creating password file...					ok
Creating the keys for the security envelope
ok
Adding the first user			Jun 11 17:25:35  info	Entry /mindstorm/user/a/admin/ does not exist in the catalogue
Jun 11 17:25:35  info	Using the default Mindstorm.cern.ch:3307/mysql/processes
Granting privileges for subho in alien_system (so far 0)
Jun 11 17:25:35  info	WE HAVE TO GIVE ACCESS TO 0
Jun 11 17:25:36  info	Creating new homedir for  subho and /proc/subho/
Jun 11 17:25:36  info	New table number: 1
Jun 11 17:25:36  info	Updating columns of table L1L
Jun 11 17:25:36  info	Creating the index UNIQUE INDEX (lfn) on the table L1L
Jun 11 17:25:36  info	Creating the index INDEX(dir) on the table L1L
Jun 11 17:25:36  info	Creating the index INDEX(guid) on the table L1L
Jun 11 17:25:36  info	Creating the index INDEX(type) on the table L1L
Jun 11 17:25:36  info	Creating the index INDEX(ctime) on the table L1L
Jun 11 17:25:36  info	Creating the index INDEX(guidtime) on the table L1L
Jun 11 17:25:36  info	How do we renumber 'L1L'??
Jun 11 17:25:36  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:36  info	How do we renumber 'L0L'??
Jun 11 17:25:36  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:36  info	Updating the INDEX table of  alien_system
Jun 11 17:25:36  info	And now, let's give access to admin to 'L1L
Jun 11 17:25:36  info	New table number: 2
Jun 11 17:25:36  info	Updating columns of table L2L
Jun 11 17:25:36  info	Creating the index UNIQUE INDEX (lfn) on the table L2L
Jun 11 17:25:36  info	Creating the index INDEX(dir) on the table L2L
Jun 11 17:25:37  info	Creating the index INDEX(guid) on the table L2L
Jun 11 17:25:37  info	Creating the index INDEX(type) on the table L2L
Jun 11 17:25:37  info	Creating the index INDEX(ctime) on the table L2L
Jun 11 17:25:37  info	Creating the index INDEX(guidtime) on the table L2L
Jun 11 17:25:37  info	How do we renumber 'L2L'??
Jun 11 17:25:37  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:37  info	How do we renumber 'L0L'??
Jun 11 17:25:37  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:37  info	Updating the INDEX table of  alien_system
Jun 11 17:25:37  info	And now, let's give access to admin to 'L2L
Jun 11 17:25:37  info	Changing privileges for  subho
The entry exists and it is called /mindstorm/user/s/subho/ (in L1L)
Jun 11 17:25:37  info	This is in fact an index!!!!
Jun 11 17:25:37  info	HERE WE SHOULD UPDATE ALSO THE FATHER
The entry exists and it is called /proc/subho/ (in L2L)
Jun 11 17:25:37  info	This is in fact an index!!!!
Jun 11 17:25:37  info	HERE WE SHOULD UPDATE ALSO THE FATHER
Jun 11 17:25:37  info	Adding the quotas
Jun 11 17:25:37  info	User subho added
Jun 11 17:25:37  info	Let's syncrhonize the DB users with ldap
Jun 11 17:25:37  info	Got the database
Jun 11 17:25:37  info	Got the ldap
Jun 11 17:25:37  info	And now, the roles
Jun 11 17:25:37  info	And let's add the new users
Jun 11 17:25:37  info	Adding the user subho
Granting privileges for subho in alien_system (so far 0)
Jun 11 17:25:37  info	WE HAVE TO GIVE ACCESS TO 0
Jun 11 17:25:37  info	Creating new homedir for  subho and /proc/subho/
Jun 11 17:25:37  info	This is already in a different table...
Jun 11 17:25:37  info	Error moving the directory /mindstorm/user/s/subho/
Jun 11 17:25:37  info	ok!!
Jun 11 17:25:37  info	Let's resync the SE and volumes from LDAP
Jun 11 17:25:37  info	Using the default Mindstorm.cern.ch:3307/mysql/transfers
Jun 11 17:25:37  info	There are 0 entries under AliEnMSS
Granting privileges for aliprod in alien_system (so far 0)
Jun 11 17:25:37  info	WE HAVE TO GIVE ACCESS TO 0
Jun 11 17:25:37  info	Creating new homedir for  aliprod and /proc/aliprod/
Jun 11 17:25:37  info	New table number: 3
Jun 11 17:25:37  info	Updating columns of table L3L
Jun 11 17:25:37  info	Creating the index UNIQUE INDEX (lfn) on the table L3L
Jun 11 17:25:37  info	Creating the index INDEX(dir) on the table L3L
Jun 11 17:25:37  info	Creating the index INDEX(guid) on the table L3L
Jun 11 17:25:37  info	Creating the index INDEX(type) on the table L3L
Jun 11 17:25:37  info	Creating the index INDEX(ctime) on the table L3L
Jun 11 17:25:38  info	Creating the index INDEX(guidtime) on the table L3L
Jun 11 17:25:38  info	How do we renumber 'L3L'??
Jun 11 17:25:38  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:38  info	How do we renumber 'L0L'??
Jun 11 17:25:38  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:38  info	Updating the INDEX table of  alien_system
Jun 11 17:25:38  info	And now, let's give access to admin to 'L3L
Jun 11 17:25:38  info	New table number: 4
Jun 11 17:25:38  info	Updating columns of table L4L
Jun 11 17:25:38  info	Creating the index UNIQUE INDEX (lfn) on the table L4L
Jun 11 17:25:38  info	Creating the index INDEX(dir) on the table L4L
Jun 11 17:25:38  info	Creating the index INDEX(guid) on the table L4L
Jun 11 17:25:38  info	Creating the index INDEX(type) on the table L4L
Jun 11 17:25:38  info	Creating the index INDEX(ctime) on the table L4L
Jun 11 17:25:38  info	Creating the index INDEX(guidtime) on the table L4L
Jun 11 17:25:38  info	How do we renumber 'L4L'??
Jun 11 17:25:38  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:38  info	How do we renumber 'L0L'??
Jun 11 17:25:38  info	There are -1 +1 entries that need to be fixed
Jun 11 17:25:38  info	Updating the INDEX table of  alien_system
Jun 11 17:25:38  info	And now, let's give access to admin to 'L4L
Jun 11 17:25:38  info	Changing privileges for  aliprod
The entry exists and it is called /mindstorm/user/a/aliprod/ (in L3L)
Jun 11 17:25:38  info	This is in fact an index!!!!
Jun 11 17:25:38  info	HERE WE SHOULD UPDATE ALSO THE FATHER
The entry exists and it is called /proc/aliprod/ (in L4L)
Jun 11 17:25:38  info	This is in fact an index!!!!
Jun 11 17:25:38  info	HERE WE SHOULD UPDATE ALSO THE FATHER
Jun 11 17:25:38  info	Adding the quotas
Jun 11 17:25:38  info	User aliprod added
Jun 11 17:25:38  info	Let's syncrhonize the DB users with ldap
Jun 11 17:25:38  info	Got the database
Jun 11 17:25:38  info	Got the ldap
Jun 11 17:25:38  info	And now, the roles
Jun 11 17:25:38  info	And let's add the new users
Jun 11 17:25:38  info	ok!!
Jun 11 17:25:38  info	Let's resync the SE and volumes from LDAP
Jun 11 17:25:38  info	Using the default Mindstorm.cern.ch:3307/mysql/transfers
Jun 11 17:25:38  info	There are 0 entries under AliEnMSS
Connecting to mysql Mindstorm.cern.ch 3307...			ok
Creating password file...					ok
Changing the ownership of /home/subho/.alien/...		ok
Checking old /home/subho/.alien/etc/aliend/startup.conf...			ok
Creating /home/subho/.alien/etc/aliend/startup.conf...				ok
Creating startup file...					ok
Starting the services...
Starting AliEn services: 
Doing Start for Mindstorm
       Service Proxy                                       ok
       Service IS                                       ok
       Service Authen                                       ok
       Service Server                                       ok
       Service Logger                                       ok
       Service Broker                                       ok
       Service TransferManager                                       ok
       Service TransferBroker                                       ok
       Service TransferOptimizer                                       ok
       Service JobOptimizer                                       ok
       Service CatalogueOptimizer                                       ok
       Service PackManMaster                                       ok
       Service MessagesMaster                                       ok
       Service SEManager                                       ok
       Service JobInfoManager                                       ok
       Service MonaLisaTrying to start MonaLisa. Please wait .... STARTED [ PID == 2362 ]
                                       ok
ok
Checking that the services are up...Error! Some services are dead!!
Status of AliEn services: 
 Doing Status for Mindstorm
        Service Proxy                                       ok
        Service IS                                       ok
        Service Authen                                       ok
        Service Server                                       ok
        Service Logger                                       ok
        Service Broker                                       ok
        Service TransferManager                                       ok
        Service TransferBroker                                       ok
        Service TransferOptimizer                                       ok
        Service JobOptimizer                                       ok
        Service CatalogueOptimizer                                       ok
        Service PackManMaster                                       ok
        Service MessagesMaster                                       ok
        Service SEManager                                       ok
        Service JobInfoManager                                       ok
        Service MonaLisaDoing PID-only check for MonaLisa... DEAD
 ERROR 1                                       failed

ERROR!!



```


any ideas??

---

### Post by josephellengar on 2010-06-11
EDIT: never mind.  different alien.

---

