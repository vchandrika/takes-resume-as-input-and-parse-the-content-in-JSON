# takes-resume-as-input-and-parse-the-content-in-JSON
chatgpt prompt which takes the resume as input and parse the content in JSON format 
This code defines a parse_resume function that takes a resume text as input, tokenizes it, extracts relevant information, and creates a JSON object to store the parsed information. The example usage shows how to use the function with a sample resume text

import json

def parse_resume(resume_text):
    # Tokenize the resume text
    tokens = [word for word in resume_text.split() if word.isalpha()]

    # Extract relevant information from the tokens
    name = ' '.join(tokens[:tokens.index('Objective')]).strip()
    objective = ' '.join(tokens[tokens.index('Objective'):tokens.index('Education')]).strip()
    education = ' '.join(tokens[tokens.index('Education'):tokens.index('Work')]).strip()
    work_experience = ' '.join(tokens[tokens.index('Work'):]).strip()

    # Create a JSON object to store the parsed information
    resume_json = {
        'name': name,
        'objective': objective,
        'education': education,
        'work_experience': work_experience
    }

    return json.dumps(resume_json)

# Example usage:
resume_text = """
John Doe
Objective: To obtain a challenging position in a reputable company
Education:
  - Bachelor's Degree in Computer Science, XYZ University (2010-2014)
Work Experience:
  - Software Engineer, ABC Company (2014-2018)
  - Senior Software Engineer, DEF Company (2018-Present)
"""

print(parse_resume(resume_text))


