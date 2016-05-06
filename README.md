# RelocaTE2: a high resolution mapping tool for transposable elements polymorphisms in large population data

## Introduction

## Installation
+ System requirements
  - Linux/Unix platform
  - Short read aligner: BLAT (v35+), bowtie (v2.2.6+), bwa (v0.6.2)
  - Python (v2.7.5+) and pysam pakcage (v0.8.5+)
  - Perl (v5.20.2+)
  - seqtk (v1.0+)

+ Install
```shell
git clone https://github.com/JinfengChen/RelocaTE2.git
cd RelocaTE2
#edit fullpath of tools in CONFIG and run testing script
vi CONFIG
uz test_data.tar.gz
cd test_data
bash RelocaTE2_run.sh > RelocaTE2_run.log 2>&1 &
```
+ Troublethrough
  - install and setup pysam in local directory
```shell
git clone https://github.com/pysam-developers/pysam.git
cd pysam
python setup.py install --prefix ~/software/tools/pythonlib
export PYTHONPATH=$PYTHONPATH:~/BigData/software/pythonlib/lib/python2.7/site-packages
```
## Quick Start Quide
  - index referene genome
```shell
#reference genome
ref=test_data/FLY603.Chr2L.fa
bwa index $ref
```
  - index repeat sequence if use bowtie2 as search engine (default is to use BLAT as search engine)
```shell
#repeat elements
repeat=test_data/pogo.fa
bowtie2-build $repeat $repeat
```
  - run RelocaTE2 to find transposable element insertions.
```shell
#repeatmasker results of TE annotation
ref_te=test_data/FLY603.Chr2L.fa.RepeatMasker.out
#directory where to put fastq format reads
fq_dir=test_data/FLY603.Chr2L.pogo.rep1_reads/
#output directory where RelocaTE2 write temperary and final output
outdir=test_data/FLY603.Chr2L.pogo.rep1_RelocaTE2_outdir
python relocaTE.py --te_fasta $repeat --genome_fasta $genome --fq_dir $fq_d --outdir $outdir --reference_ins $ref_te 
```

## RelocaTE2 Command Line Options

## RelocaTE2 input

## RelocaTE2 output

## 
