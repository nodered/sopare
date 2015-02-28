This is the **SO**und **PA**ttern **RE**cognition project written in Python.
Currently the project is in a very early stage and best it can be described as prototype.
In a nutshell the project listens endless and compares the input based on simple characteristics
with entries stored in a dictionary. The output is an array with some information about a potential match.
Here is an example output when I said the word computer twice:

`
Match = [[0, u'computer', 100, 'psel']]
Match = [[1, u'computer', 100, 'psel']]
`

More background information: https://sway.com/BQ8uXDse9LLhL0Zf


Scope and goals:
 
  * Real time audio processing
  * Must run on small credit card sized, ARM powered computers like Rasbberry Pi, Banana Pi and alike
  * Pattern/voice recognition for only a few words
  * Must work offline without immanent dependencies to cloud APIs


Examples of use:

  * (Smart) home control
  * Voice controlled robots
  * Can be used in combination with any available cloud API or service like
     http://stevenhickson.blogspot.de/2013/06/voice-command-v30-for-raspberry-pi.html
     http://www.vocapia.com/speech-to-text-api.html
     (and many more)
     e.g. to rate input upfront
  

Dependencies:

  * Python
  * pyaudio (apt-get install python-pyaudio)
  * numpy (apt-get install python-numpy)
  * mathplot (apt-get install python-matplotlib)

  
Installation:

 Just checkout the project and resolve the dependencies:

 git clone https://github.com/bishoph/sopare.git .


Usage:

`
Show the available options
python sopare.py --help

The next command turns the verbose mode on, waits for a peak,
records the input and saves it in raw form to the file 
"samples/computer.raw", finds the characteristic and adds the
word "computer" to the dictionary, plots the results and stops.
If you run the same command more often, existing entries in
the dictionary are updated if a change is detected (learn).
Learning and adding new words to the dictionary requires
a silent environment. Of course you can change and adopt
the entries manually as the dictionary is stored in 
JSON format.

python sopare.py -p -v -o samples/computer.raw -l computer


This command listens endless and compares the input with 
dictionary entries and prints out the results. The program
tries to tokenize the input to detect single words. 
Currently the "tokens" are converted into "tokenN.wav" files
so that you can debug. There are some config options
available when you look into the code ;)

python sopare.py -e


You can delete the newly created entry from the dictionary
simple by running the command

python sopare.py -d computer
`

