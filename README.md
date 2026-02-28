# ENA Downloader

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

Command-line tool for downloading sequencing data and metadata from the European Nucleotide Archive (ENA).

## Features

- Download FASTQ files from ENA projects, runs, or experiments
- Fetch genome assemblies (GCA/GCF accessions)
- Download nucleotide and protein sequences
- Retrieve sample and project metadata
- Progress tracking with speed statistics
- MD5 checksum verification
- Automatic directory organization
- Resume interrupted downloads

## Supported Accession Types

| Type | Pattern | Example |
|------|---------|---------|
| Project | PRJEB*, PRJNA*, SRP* | PRJNA123456 |
| Run | ERR*, SRR*, DRR* | ERR1234567 |
| Experiment | ERX*, SRX* | SRX123456 |
| Assembly | GCA_*, GCF_* | GCA_002870075.4 |
| Sample | SAMEA*, SAMN* | SAMEA123456 |
| Sequence | Various | AB123456.1 |

## Installation

```bash
uv sync
```

## Usage

### List files for a project

```bash
uv run ena-download PRJNA123456
```

### Download all FASTQ files

```bash
uv run ena-download PRJNA123456 --download
```

### Download a genome assembly

```bash
uv run ena-download GCA_002870075.4 --download
```

### Filter files by pattern

```bash
uv run ena-download PRJNA123456 --download --pattern ".*_1.fastq.gz"
```

### Download with metadata

```bash
uv run ena-download PRJNA123456 --download --metadata
```

## Options

| Option | Description |
|--------|-------------|
| `--download` | Download files (default: list only) |
| `--pattern` | Regex to filter files |
| `--exclude` | Regex to exclude files |
| `--output-dir` | Output directory (default: ena_downloads) |
| `--max-files` | Limit number of files |
| `--metadata` | Fetch and save metadata |
| `--force-download` | Re-download existing files |
| `--use-submitted` | Use original submitted files |

## Output Structure

Downloads are organized by accession:

```
ena_downloads/
  PRJNA123456/
    raw-data/
      ERR123456_1.fastq.gz
      ERR123456_2.fastq.gz
    metadata/
      PRJNA123456_metadata.json
```

## License

MIT License
