---
title: "python sqlite"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by saj_123 on 2009-04-08
Hi
im new to using python and sqlite. can anyone help me. iv designed a program to capture network packets, then dependent on the ip protocol it will either store the data in a tcp table or udp table. im trying to do a caluclation which will calculate the percentage of the tcp or udp packets it has captured.

	cursor = db.cursor()
	cursor.execute ("select * from tcptable")
	row = cursor.fetchall()
	tcp = len(row)
	cursor.execute ("select * from udptable")
	row = cursor.fetchall()
	udp = len(row)
	total = udp + tcp
	print row
	tcpPercentage = (tcp / total) * 100
	udpPercentage = (udp / total) * 100
	print '%s%% , %s%%' % (tcpPercentage, udpPercentage)

this is the code i have used. it works fine if all the packets are captured are tcp then it will return 100%, 0% but if there are any udp packets it will return 0%, 0%. any help wud be much appreciated.

---

### Post by Hospadar on 2009-04-08
Well first off all, are you sure the problem isn't when the data goes into your database?

let's say your sqlite db is name db.sqlite3
on the command line:
sqlite3 db.sqlite3
(now you'll get the sqlite prompt)
SELECT COUNT(*)  FROM tcptable;
SELECT COUNT(*) FROM udptable;

Do you get the values you expect? (by the way, right now as you're just counting rows, it would be a lot more efficient to use count(*) instead of just selecting all and counting the rows yourself) 

Other than that though your code looks fine to me, try just printing out all the values at every point and see what you get.

Also, do you know about debugging in python?

You can "import pdb" at the top of the file, then insert a "pdb.set_trace()" where you want the code to break.  when it breaks you get a python command line and you can print out whatever variables you want, and step through the program line by line.

---

### Post by saj_123 on 2009-04-08
```
import sys #for command line arguments
import sqlite3 #database
#try and import scapy for different versions
try:
	from scapy.all import sniff #new
except ImportError:
	from scapy import sniff #old
	
def main(argv):

	if len (argv) !=1:
		print "No parameter passed"
		exit()
	x=int(argv[0])
	packet=sniff(count=x,filter="tcp || udp", prn=lambda x: x.show())
	Max = len(packet)

	connection = sqlite3.connect('packetdb')
	db = sqlite3.connect('packetdb', isolation_level=None)
	db.execute ("DROP TABLE tcptable")
	db.execute ("DROP TABLE udptable")
	db.execute ("CREATE TABLE IF NOT EXISTS tcptable (id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,Ether_Dst VARCHAR, Ether_Src VARCHAR, IP_Flags VARCHAR, IP_Protocol VARCHAR, IP_Src INTEGER, IP_Dst INTEGER, TCP_Sport VARCHAR, TCP_Dport INTEGER, TCP_ack INTEGER, TCP_flags VARCHAR)")
	db.execute ("CREATE TABLE IF NOT EXISTS udptable (id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,Ether_Dst VARCHAR, Ether_Src VARCHAR, IP_Flags VARCHAR, IP_Protocol VARCHAR, IP_Src INTEGER, IP_Dst INTEGER, UDP_Sport VARCHAR, UDP_Dport VARCHAR)")
	db.close()

	for P in range (0,Max):
		db = sqlite3.connect('packetdb', isolation_level=None)
		print "Packet Number: %s" % (P+1)
		ethernet_dst= packet[P].sprintf("%Ether.dst%")
		ethernet_src= packet[P].sprintf("%Ether.src%")
		print "Ethernet Destination: %s | Ethernet Source: %s" % (ethernet_src,ethernet_dst)
		ip_flags= packet[P].sprintf("%IP.flags%")
		print "Flags: %s" % (ip_flags)
		ip_proto= packet[P].sprintf("%IP.proto%")
		print "protocol: %s" % (ip_proto)
		ip_src= packet[P].sprintf("%IP.src%")
		ip_dst= packet[P].sprintf("%IP.dst%")
		print "IP source: %s | IP Destination : %s" % (ip_src, ip_dst) 
		tcp_sport= packet[P].sprintf("%TCP.sport%")
		tcp_dport= packet[P].sprintf("%TCP.dport%")
		print "destination port: %s | source port: %s" % (tcp_dport, tcp_sport)
		tcp_ack= packet[P].sprintf("%TCP.ack%")
		print "acknowledge: %s" % (tcp_ack)
		tcp_flags= packet[P].sprintf("%TCP.flags%")
		print "TCP flags: %s" % (tcp_flags)
		udp_sport= packet[P].sprintf("P.sport%")
		udp_dport= packet[P].sprintf("P.dport%")
		print "destination port: %s | source port: %s" % (udp_dport,udp_sport)
				
		if ip_proto =='tcp':
			db.execute("INSERT INTO tcptable (Ether_Dst,Ether_Src,IP_Flags, IP_Protocol,IP_Src,IP_Dst,TCP_Sport,TCP_Dport, TCP_ack, TCP_flags) VALUES ('%s','%s','%s','%s','%s','%s','%s','%s','%s','%s')" %(ethernet_dst,ethernet_src,ip_flags,ip_proto,ip_src,ip_dst,tcp_sport,tcp_dport,tcp_ack,tcp_flags))	
			results = db.execute("select * FROM tcptable").fetchall()

			for row in results:
				print row[0], row[1], row[2]
	
		elif ip_proto == 'udp':
			db.execute("INSERT INTO udptable (Ether_Dst,Ether_Src,IP_Flags, IP_Protocol,IP_Src,IP_Dst,UDP_Sport,UDP_Dport) VALUES ('%s','%s','%s','%s','%s','%s','%s','%s')" % (ethernet_dst,ethernet_src,ip_flags,ip_proto,ip_src,ip_dst,udp_sport,udp_dport))
			results = db.execute("select * FROM udptable").fetchall()
			for row in results:
				print row[0], row[1], row[2]
								
	cursor = db.cursor()
	cursor.execute ("select * from tcptable where TCP_Sport== 'www'")
	row = cursor.fetchall()
	for item in row:
		print item
			
	cursor = db.cursor()
	cursor.execute ("select * from tcptable")
	row = cursor.fetchall()
	tcp = len(row)
	cursor.execute ("select * from udptable")
	row = cursor.fetchall()
	udp = len(row)
	total = udp + tcp
	print row
	tcpPercentage = (tcp / total) * 100
	udpPercentage = (udp / total) * 100
	print '%s%% , %s%%' % (tcpPercentage, udpPercentage)
			
if __name__ == "__main__":
	main(sys.argv[1:])

```
	





this is all the code i am using. it is storing everythin i expect in the database. its just in the terminal its not displaying the calulcations properly.

---

