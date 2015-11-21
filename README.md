# A Question Generator.
Author: Mengye Ren  Email: mren@cs.toronto.edu

## Usage
    python question_generator.py \
            -parser_path {Stanford parser path} \
            -sentence {Single sentence} \
            -list {List of sentences, line dilimited file} \
            -parsed_file {Parsed file generated by stanford parser} \
            -output {Output file}

## Prerequisites
1. You need to download NLTK WordNet package.
'''
>> python
>> import nltk
>> nltk.download()
>> d
>> wordnet
'''

2. You need to download Stanford Parser
at http://nlp.stanford.edu/software/lex-parser.shtml#Download
Extract the zip into a folder and remember the path

3. You need to copy lexparser_sentence.sh into the Stanford Parser folder.
'''
cp lexparser_sentence.sh stanford-parser/lexparser_sentence.sh
'''

## Examples
1. Run single sentence.
'''
python question_generator.py -sentence "A man is riding a horse"
'''

2. Run a list of sentences.
Provide a file with each line in the file to be a sentence.
Output is a pickle file, storing a list. Each element in the list is a
tuple of five fields:
- Original sentence ID (0-based)
- Original sentence
- Generated question
- Answer to the generated question
- Type of the generated question

'''
python question_generator.py -list sentences.txt -output questions.pkl
'''

3. Run a pre-parsed file.
Run stanford parser to pre-compute the parse trees.

'''
lexparser.sh sentences.txt > sentences_parsed.txt
'''

'''
python question_generator.py -list sentences.txt \
                             -parsed_file sentences_parsed.txt \
                             -output questions.pkl
'''

## Reference
'''
@inproceedings{ren2015imageqa,
  title={Exploring Models and Data for Image Question Answering},
  author={Mengye Ren and Ryan Kiros and Richard Zemel},
  booktitle={NIPS},
  year={2015}
}
'''