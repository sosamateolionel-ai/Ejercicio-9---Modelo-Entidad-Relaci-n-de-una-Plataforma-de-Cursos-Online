# Ejercicio 9 - Modelo Entidad-Relación de una Plataforma de Cursos Online

## Descripción
Este ejercicio consiste en diseñar un modelo Entidad-Relación (DER) para un sistema de gestión de e-learning o plataforma de cursos online. El modelo permite administrar instructores, cursos, módulos, lecciones, estudiantes, inscripciones, evaluaciones y el seguimiento de intentos de evaluación.

## Entidades y atributos

### 1. Instructor
Representa a los docentes o instructores que dictan los cursos.
- **id_instructor**: identificador único del instructor.
- **especialidad**: área de especialización del instructor.
- **mail**: correo electrónico de contacto.
- **nombre**: nombre completo del instructor.
- **biografia**: resumen del perfil o trayectoria profesional.

### 2. Curso
Representa los cursos disponibles en la plataforma.
- **id_curso**: identificador único del curso.
- **id_instructor**: identificador del instructor a cargo.
- **titulo**: título del curso.
- **descripcion**: detalle de los temas abordados.
- **precio**: costo de inscripción al curso.
- **dificultad**: nivel de dificultad (ej. principiante, intermedio, avanzado).

### 3. Modulo
Representa los bloques o temas principales en los que se divide un curso.
- **id_modulo**: identificador del módulo.
- **id_curso**: identificador del curso al que pertenece.
- **titulo**: nombre o título del módulo.
- **orden**: secuencia o posición del módulo dentro del curso.

### 4. Leccion
Representa las lecciones o clases individuales contenidas en cada módulo.
- **id_leccion**: identificador de la lección.
- **id_modulo**: identificador del módulo al que pertenece.
- **titulo**: título de la lección.
- **tipo**: tipo de material (ej. video, lectura, recurso).
- **duracion**: tiempo estimado de duración.
- **contenido**: cuerpo o enlace del contenido.
- **orden**: secuencia de la lección dentro del módulo.

### 5. Estudiante
Representa a los usuarios matriculados en la plataforma.
- **id_estudiante**: identificador único del estudiante.
- **id_inscripcion**: identificador de la inscripción vinculada.
- **nombre**: nombre completo del estudiante.
- **email**: correo electrónico.
- **ingreso**: fecha de registro o alta en la plataforma.

### 6. Inscripcion
Entidad asociativa que gestiona el registro y progreso de un estudiante en un curso.
- **id_estudiante**: identificador del estudiante.
- **id_curso**: identificador del curso.
- **fecha**: fecha en que se realizó la inscripción.
- **progreso**: porcentaje o nivel de avance en el curso.
- **estado finalizacion**: estado de la cursada (ej. en curso, completado, abandonado).

### 7. Evaluacion
Representa los exámenes o pruebas asignados a los cursos.
- **evaluacion**: nodo principal que define la evaluación del curso.

### 8. Pregunta
Representa las preguntas individuales que integran una evaluación.
- **id_pregunta**: identificador de la pregunta.
- **id_evaluacion**: identificador de la evaluación asociada.
- **enunciado**: texto o consigna de la pregunta.
- **puntaje**: valor en puntos asignado a la pregunta.
- **cantidad**: cantidad u opciones asociadas.

### 9. Intento evaluacion
Representa los intentos realizados por los estudiantes al rendir una evaluación.
- **id_intento**: identificador único del intento.
- **id_estudiante**: identificador del estudiante que rinde.
- **id_evaluacion**: identificador de la evaluación rendida.
- **numero intento**: número de intento de evaluación.
- **calificacion**: nota obtenida en el intento.
- **estado**: resultado o estado del intento (ej. aprobado, desaprobado).

## Relaciones y cardinalidades
- **Instructor – Curso (Tiene / 1:N)**: un instructor puede impartir múltiples cursos.
- **Curso – Modulo (Contiene / 1:N)**: un curso se compone de uno o varios módulos.
- **Modulo – Leccion (Contiene / 1:N)**: un módulo abarca múltiples lecciones estructuradas ordenadamente.
- **Curso – Estudiante (Inscribe / Genera / 1:N)**: gestiona la matriculación de los estudiantes en los cursos a través de la relación de **Inscripcion**.
- **Curso – Inscripcion (Necesita / 1:1)** e **Inscripcion – Evaluacion (Incluye / 1:1)**: vincula la cursada e inscripción del alumno con la respectiva evaluación del programa.
- **Evaluacion – Pregunta (Tiene / 1:N)**: una evaluación contiene un conjunto de preguntas.
- **Estudiante – Intento evaluacion (Realiza / 1:N)**: un estudiante puede realizar múltiples intentos para resolver las evaluaciones.
- **Evaluacion – Intento evaluacion (Rinde / 1:N)**: una evaluación registra todos los intentos llevados a cabo por los alumnos.

## Objetivo
Diseñar una base de datos funcional para una plataforma e-learning que permita estructurar el contenido programático de los cursos (módulos y lecciones), controlar las inscripciones y el avance de los estudiantes, y administrar el sistema de evaluaciones junto con el registro de calificaciones de los alumnos.
