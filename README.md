# asterisk-picotts
Asterisk Gateway Interface (AGI) script to enable PicoTTS text-to-speech engine to be called from the dialplan of an Asterisk server running on a Raspberry Pi.

------------
Installation
------------
(Assuming running on an existing RasPBX installation - http://www.raspberry-asterisk.org/)
First, install the PicoTTS libraries:
 - sudo apt-get install libttspico0
 - sudo apt-get install libttspico-utils
 
Then copy the picotts.agi file to Asterisk's agi-bin directory (by default, this is /var/lib/asterisk/agi-bin)
- if unsure, check the directory specified in /etc/asterisk/asterisk.conf

------------
Usage
------------
agi(picotts.agi,"text",[language],[intkey],[speed])
This will invoke the PicoTTS engine, render the text string to speech and play it back to the user.

--------
Examples
--------

; Answer the call
exten => 1234,1,Answer()
; Play mesage in English:
 same => n,agi(picotts.agi,"This is a simple text to speech test in english.",en-GB)
; End the call
 same => n,Hangup()
